---
layout: post
title: Building a Secure Go Server for My AWS Lambda Microservices
description: An opportunity to learn a new language!
date: 2025-04-01
tags: [AWS, growth, programming]

comments: true
published: true

---

Now that my RDS database is working and I can connect to it directly from my local machine via an SSH tunnel, I've started developing my application. Given the architecture I have in mind, I expect to have multiple AWS Lambda functions acting as microservices.

One straightforward approach would be to have these Lambda functions interact directly with the database using SQL queries. However, this poses security risks - SQL statements would be embedded within the Lambda functions, making them visible and potentially susceptible to manipulation.

To mitigate this risk and ensure the integrity of my application logic, I've decided to build a dedicated server that will act as an intermediary between the Lambda functions and the database.

The easiest way for me to do this would be by setting up a Django server, given my experience developing chatbot APIs and other backend services with it. However, one of my goals for 2025 is to learn a new programming language, and I've chosen to build this server in Golang. There's no specific reason for picking Go over Java or C++, aside from my personal interest in it.

I had previously dabbled in Golang and understood the basic syntax, but I never had the opportunity to work with it extensively, as my team primarily uses Python. With the help of ChatGPT and Perplexity, I managed to develop a basic Go server. Troubleshooting the database connection was challenging, but I ultimately got it working.

With the Go server now running on my local machine, I had two possible paths forward:
1. Deploy the server on AWS EKS, configure it to connect to the RDS database (both locally and on EKS), and finalize the Dockerfile to build the container image.
1. Focus on developing a fully functional Go server that meets all my initial requirements before worrying about deployment.

Initially, I pursued the first option for a few days. However, as I worked through the deployment and troubleshooting process, I realized that EKS costs were higher than expected. The cluster was running on relatively large EC2 instances, which could amount to around $100 per month if left unchecked. Given that I wouldn't be using the Go server on EKS 24/7 at the moment, keeping it idle would be an unnecessary expense.

As a result, I decided to pause the EKS deployment and shift my focus toward building a fully functional Go server first. This approach is both more productive and cost-effective.

