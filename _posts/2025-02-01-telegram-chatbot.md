---
layout: post
title: Building a Telegram Chatbot with AWS Lambda
description: What a fun challenge!
date: 2025-02-01
tags: [technical, programming, project, AWS]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']

comments: true
published: false

---
One of my exciting [plans for 2025](https://brandonyongys.github.io/blog/2025/setting-my-goals/) is to develop a simple Supermarket chatbot, and after reflecting on my current knowledge, I initially thought of using WhatsApp for its implementation since I have prior experience with it at work. However, I quickly realized that using WhatsApp might not be the most efficient option, as it would involve additional third-party software and could become quite costly.

That being said, what fun would it be if I built the chatbot using what I already know? To challenge myself, I’ve decided to build the chatbot on Telegram instead. Not only does Telegram offer a fresh challenge, but it also has a larger following among younger audiences, which would help me connect with a wider user base.

# Creating Telegram Bot
The first step in building this chatbot is creating a Telegram bot, which can easily be done by chatting with @BotFather on Telegram. BotFather will guide you through the process, and the basic command to create a new bot is `/newbot`. After creating the bot, save the bot token for future use.

# Connecting Bot to AWS Lambda
To handle the interaction between users and the bot, I’ve chosen to use AWS Lambda. This allows me to scale the bot while controlling the session flow. The following Lambda function receives user messages and sends back a simple reply:

~~~
import json
import requests
import os

TELEGRAM_TOKEN = os.getenv("TELEGRAM_TOKEN")

def send_message(chat_id, text):
    url = f"https://api.telegram.org/bot{TELEGRAM_TOKEN}/sendMessage"
    payload = {"chat_id": chat_id, "text": text}
    requests.post(url, json=payload)

def lambda_handler(event, context):
    body = json.loads(event["body"])
    print(f"body: {body}")
    
    if "message" in body:
        chat_id = body["message"]["chat"]["id"]
        text = body["message"]["text"]

        # Custom response
        response_text = f"You said: {text}"
        send_message(chat_id, response_text)

    return {"statusCode": 200, "body": "OK"}

~~~

After deploying the code to AWS Lambda, the next step is setting up an API Gateway. A simple HTTP API should suffice to minimize costs according to the [Amazon API Gateway pricing](https://aws.amazon.com/api-gateway/pricing/). Remember to create three stages: dev, staging, and prod for different environments. You should also create separate API gateways for each environment, just as you would for a dev, staging, and prod version of the chatbot.

# Configuring the API Gateway
Once the gateway is set up, you need to create a route for the POST method and connect the webhook to your Lambda function. This ensures that every new message sent to your Telegram bot is forwarded to the Lambda function for processing.

# Set up Telegram Webhook
The final step is to configure the webhook for the bot. First, retrieve the URL for your API Gateway. Once you have the URL, use the following `curl` command to set up the webhook:

~~~
curl -X POST "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/setWebhook?url=<API_GATEWAY_URL>"
~~~

If everything is set up correctly, the response will be: 
~~~
{"ok":true,"result":true,"description":"Webhook is already set"}
~~~

With that, your Telegram bot is successfully connected to AWS Lambda! When you test it, the bot should reply with a message in the format: `You said: {text}`.

