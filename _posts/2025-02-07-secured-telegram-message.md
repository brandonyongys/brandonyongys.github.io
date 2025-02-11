---
layout: post
title: Securing My Telegram Bot
description: Preventing unauthorized requests
date: 2025-02-07
tags: [technical, programming, project, AWS]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']

comments: true
published: true

---
After setting up and connecting my Telegram bot to AWS, I realized that my API Gateway was exposed to potential threats. Anyone who discovers the API Gateway URL could send unauthorized requests, flood it with spam (DDoS), or attempt to exploit vulnerabilities in user inputs.

To enhance security, I implemented a simple but effective measure: adding a secret token to my Telegram webhook request.

# Adding a secret token
First, I generated a random secret token using Python:
~~~
import secrets
print(secrets.token_hex(32))
~~~

Next, I updated my Telegram webhook with the following `curl` command:
~~~
curl -X POST "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/setWebhook?url=<API_GATEWAY_URL>?secret=<SECRET_TOKEN>"
~~~

Finally, I modified my AWS Lambda function to verify the secret token before processing any requests:
~~~
query_params = event.get("queryStringParameters", {})
received_token = query_params.get("secret")

if received_token != TELEGRAM_SECRET:
    print(f"Unauthorized request!")
    return {"statusCode": 403, "body": "Forbidden"}  # Reject unauthorized requests
~~~

# Further Thoughts
While this doesn't fully protect against all threats, it ensures that only requests coming from my Telegram bot are processed, preventing unauthorized access and unnecessary AWS resource consumption during development.

Of course, more advanced security measures-such as rate limiting, IP allowlists, or input validation-would be necessary as the chatbot evolves, but for now, this simple addition provides a good starting point.
