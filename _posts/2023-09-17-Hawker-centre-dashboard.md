---
layout: post
title: Singapore Hawker Centre Dashboard
description: Want to know when your favourite hawker is closing?
date: 2023-09-17
tags: [technical, programming, project]

comments: true
published: true
---

About a year ago, I developed a `plotly` dashboard to visualize the current status as well as the next closure date for hawker centres across Singapore after I was inspired by the [post](https://towardsdatascience.com/creating-a-web-application-to-analyse-dengue-cases-1be4a708a533) by Benedict Soh on Dengue fever. 

Back then, the app was rather rudimentary and I was following Ben's codes quite closely as I wanted to develop and deploy a simple app. The deployment was done using Heroku free tier. Unfortunately, Heroku decided to shut down their free tier from 28 Nov 2022 onwards. Talk about timing! Since then, I took it down and didn't deploy it anyway as I didn't have free time to find out alternatives.  

At the start of 2023, I started to look into AWS certificates and prepared for AWS Cloud Practitioner certificate, which I have passed back in Feb 2023. Now I am working towards AWS Solutions Architect Associate certificate and I do find it challenging especially since I have rather limited experience with it. This is a blessing in disguise as I could take this opportunity to learn more with AWS and gain hands on experience by redeploying my apps on AWS. 

At the same time, I also decided to work with Docker (finally! It is a shame to not know Docker as a IT professional :P).  

# App improvement
1. Data input via API

Previously the data came from some csv flat files that I had to check and download periodically. That can be rather troublesome and recommended. Instead, I changed codes to fetch the latest data using API endpoint. Thereafter, the data is preprocessed in the same fashion.

2. App refresh

The previous app was a static dashboard and could not update itself especially when a new day comes. The new dashboard will now refreshes itself as and when the user refreshes the browser by assigning the `app.layout` as the `update_layout` where`update_layout` is the function used to call the eventual dashboard. With this, the map as well as the datatable content will update according to the date. The solution

3. Datatable instead of static table

The previous tables were static table and there was no filtering capability. I have since converted them into datatable using `dash_table.DataTable` instead of `dbc.Table`. Now the user could filter for their hawker centre or find out which hawker is closing soon etc.

4. Reorganization of codes

The previous set of codes was rather messy as I would lump up almost the entire operations within the same `.py` file. Now, I have clearly separated them so that I know what is used to call and process the data and what is used to visualize the data. It is simply more organized!

5. Dashboard aesthestic

Lastly is just the aesthestic of the dashboard. Previously I was using the same style as Benedict's dashboard. Now I have updated it to follow Singapore flag colour codes. After all, the dashbaord is about *Singapore* hawker centres. I've also formatted the data table so that it is aesthetically pleasing and less messy. However, this is a very subjective improvement as you may think the previous version is much better looking.


# AWS deployment
The dashboard is ultimately deployed using AWS. There are many ways to deploy them but I decided to use Docker image and Amazon ECS. 

Firstly I would package the entire app as a Docker image using a Dockerfile before pushing it to Amazon ECR. Once the image is pushed to Amazon ECR, I would then build the entire stack by creating a cluster on Amazon ECS. I referenced this [post](https://towardsdatascience.com/how-to-use-docker-to-deploy-a-dashboard-app-on-aws-8df5fb322708) on Medium for deployment step by step.

The app is ultimately deployed on [http://3.0.104.136/](http://3.0.104.136/). 

# Final thoughts
This project is a rather simple project yet it has introduced me to important concepts such as working with API endpoints and AWS deployment. All these concepts are important, not just to a data scientist, but also to IT practitioners out there. 

This is gonna be the first of many projects I will be working towards for deployment.