---
title : "Install streamlit application"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---


### Update the system and install python
```
sudo yum update -y
sudo yum install python3
sudo yum install pip
sudo yum install python3-venv

``` 
### Install virtual env
```
python3 -m venv appEnv  # Tạo môi trường ảo tên là appEnv 
```
### Install the library
```
source appEnv/bin/activate  # Kích hoạt môi trường ảo
pip install streamlit requests boto3 mysql-connector-python
pip3 list
```
### Create file app.py
```
touch app.py
vi app.py
```

```python
import json
import boto3
import streamlit as st
import mysql.connector

# Function to connect to RDS MySQL primary database
def connect_to_primary_db():
    connection = mysql.connector.connect(
        host="database-primary-chatbot.cxksqi0gs55d.us-east-1.rds.amazonaws.com",
        user="admin",
        password="12345678",  # Replace with your actual password
        database="conversation_db"  # Replace with your actual database name
    )
    return connection

# Function to connect to RDS MySQL read replica database
def connect_to_read_replica_db():
    connection = mysql.connector.connect(
        host="database-read-chatbot.cxksqi0gs55d.us-east-1.rds.amazonaws.com",  # Replace with your Read Replica endpoint
        user="admin",
        password="12345678",  # Replace with your actual password
        database="conversation_db"  # Replace with your actual database name
    )
    return connection

# Function to insert chat data into the primary database
def insert_conversation(user_message, bot_response):
    try:
        conn = connect_to_primary_db()
        cursor = conn.cursor()
        
        query = "INSERT INTO chat_conversations (user_message, bot_response) VALUES (%s, %s)"
        cursor.execute(query, (user_message, bot_response))
        conn.commit()
    except mysql.connector.Error as err:
        st.write(f"Error: {err}")
    finally:
        if conn.is_connected():
            cursor.close()
            conn.close()

# Function to fetch the last 3 conversations from the read replica
def fetch_last_conversations():
    try:
        conn = connect_to_read_replica_db()
        cursor = conn.cursor()
        query = "SELECT user_message, bot_response FROM chat_conversations ORDER BY id DESC LIMIT 3;"
        cursor.execute(query)

        rows = cursor.fetchall()
        return rows
    except mysql.connector.Error as err:
        st.write(f"Error: {err}")
        return []
    finally:
        if conn.is_connected():
            cursor.close()
            conn.close()

# Streaming response message
def parse_stream(stream):
    full_response = ""  # Initialize an empty string to hold the full response
    for event in stream:
        chunk = event.get("chunk")
        if chunk:
            message = json.loads(chunk.get("bytes").decode())
            if message["type"] == "content_block_delta":
                full_response += message["delta"]["text"] or ""
            elif message["type"] == "message_stop":
                break
    return full_response  # Return the full response

# Create Bedrock client
client = boto3.client("bedrock-runtime", region_name="us-east-1")
# Define model id (Claude 3 Sonnet)
model_id = "anthropic.claude-3-sonnet-20240229-v1:0"

# Set page title
st.title("Amazon Bedrock Claude3 Response Streaming Demo")

# User input
prompt = st.text_input("Prompt")

if st.button("Submit"):
    if prompt:  # Ensure that prompt is not empty
        # Prepare request body
        body = json.dumps(
            {
                "anthropic_version": "bedrock-2023-05-31",
                "max_tokens": 1024,
                "messages": [
                    {
                        "role": "user",
                        "content": [{"type": "text", "text": prompt}],
                    }
                ],
            }
        )

        # Call Bedrock API and stream response  
        streaming_response = client.invoke_model_with_response_stream(
                modelId=model_id,
                body=body,
        )

        # Output response to GUI
        st.subheader("Output stream", divider="rainbow")
        bot_response = parse_stream(streaming_response.get("body"))

        # Insert the conversation into the primary database
        insert_conversation(prompt, bot_response)

        # Display the full bot response
        st.write(bot_response)

# Button to show last 3 conversations
if st.button("Show Last 3 Conversations"):
    st.subheader("Last 3 Conversations")
    last_conversations = fetch_last_conversations()
    for user_message, bot_response in last_conversations:
        st.write(f"You: {user_message}")
        st.write(f"Bot: {bot_response}")

```

### Install MySQL
```
sudo wget https://dev.mysql.com/get/mysql80-community-release-el9-1.noarch.rpm
sudo dnf install mysql80-community-release-el9-1.noarch.rpm -y
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023
sudo dnf install mysql-community-client -y
sudo dnf install mysql-community-server -y
mysql --version
```
### Create table, db
```
mysql -h database-primary-chatbot.cxksqi0gs55d.us-east-1.rds.amazonaws.com -u admin -p
```
* Type the password.
```
CREATE DATABASE conversation_db;
USE conversation_db;
CREATE TABLE chat_conversations (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_message TEXT NOT NULL,
    bot_response TEXT NOT NULL,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
exit
```

### Create services streamlit
```
sudo vi /etc/systemd/system/streamlit-app.service

[Unit]
Description=Streamlit App
After=network.target

[Service]
User=ec2-user
WorkingDirectory=/home/ec2-user
Environment="PATH=/home/ec2-user/appEnv/bin"
ExecStart=/home/ec2-user/appEnv/bin/streamlit run /home/ec2-user/app.py --server.port 8080
Restart=always

[Install]
WantedBy=multi-user.target

sudo systemctl daemon-reload
sudo systemctl enable streamlit-app.service
sudo systemctl start streamlit-app.service
sudo systemctl status streamlit-app.service
sudo reboot
sudo systemctl status streamlit-app.service
```