---
layout: post
title: Building a Basic Telegram Chatbot
# description: An opportunity to learn a new language!
date: 2025-04-07
tags: [AWS, project, technical]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']

comments: true
published: true

---

# The past
Back in February, I started exploring the Telegram API and put together a simple chatbot that echoed back whatever users typed - nothing more than a playful `You said: {text}` interaction. While it started off as a toy project, I had a more meaningful goal in mind: to build a Telegram chatbot that lets users query supermarket product prices and get information about various financial products available in Singapore.

# The present
![chatbot_architecture](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/assets/img/2025-imgs/overall_architecture.png?raw=true)

The next step was laying the groundwork for a more scalable and maintainable chatbot. The architecture I've designed is shown above.

Here's how the flow works:
1. A user sends a message to the Telegram chatbot.
1. The message is received via a webhook and passed through an API Gateway to my handler bot.
1. The handler bot enriches the payload by retrieving the session state from DynamoDB and appending relevant metadata.
1. The enriched message is routed to a set of AWS Lambda functions for preprocessing and logic execution.
1. Once a response is generated, another Lambda handles sending the reply back to the user.
1. The full conversation is archived in an S3 bucket for long-term storage and potential downstream analysis.
1. Finally, the session state is updated back into DynamoDB.

While Amazon Lex could've been an option for session state management, I've opted for a custom implementation. Based on prior experience, Lex's benefits are mostly centered around session tracking - and in this case, building a lightweight and modular system from scratch gave me greater flexibility without the overhead.

One current drawback I've observed is latency. Because of the microservice architecture, it can take up to 4 seconds for a full round-trip message - from the user's input to the final reply. This lag is largely due to cold starts in AWS Lambda. To address this, I plan to explore provisioned concurrency for the Lambdas involved in the core message processing path.

# The future
With two core use cases in mind - supermarket product queries and financial product information - the next milestones in this project are:

1. Financial Product Querying

    I plan to implement a Retrieval-Augmented Generation (RAG) pipeline to enable users to ask questions about various financial products available in Singapore. This will include embedding relevant documents, setting up a vector store, and integrating conversational context to deliver meaningful responses through the chatbot.

1. Supermarket Price Lookup

    To support real-time product price queries, I'll first build a data scraping and preprocessing pipeline that pulls data from major supermarket websites in Singapore. Once the data ingestion and cleaning steps are in place, I'll integrate this functionality into the chatbot to allow users to search for specific products or compare prices across different stores.

<hr>

This project is still evolving, and I'm excited to see how it shapes up as I build out the core features. 