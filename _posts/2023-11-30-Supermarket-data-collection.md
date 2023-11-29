---
layout: post
title: An effort to collect product details from the major supermarket chains
# description: Want to know when your favourite hawker is closing?
date: 2023-11-30
tags: [AWS, python, database]

comments: true
published: true
---
## The idea
With the rising cost of living here in Singapore, I figure it would be nice to visualize and understand how the price has changed over time for a particular product. However, this information is not easily found since companies would secretly change (or at least without me knowing) and hope that the consumers wouldn't notice it. I could always look up the product price at a particular time but not over time.

To capture this information, I have developed a simple pipeline to collect the data automatically and store them in a database. The data is collected from the major supermarkets in Singapore - namely NTUC Fairprice, Sheng Siong and Cold Storage. Admitedly Sheng Siong and Cold Storage are serving slightly different consumer segments - Sheng Siong for the common people and may not carry as many products as Fairprice and Cold Storage for the more 'atas' people with their imported products. All in all, all 3 supermarkets do not overlap 100% but it gives a good gauge for the major products such as meat, vegetables and snacks.

This pipeline is definitely something new for me especially since I have never built such a thing before as a data scientist. I have always had the luxury of working with curated datasets for my own data analytics and machine learning projects. This end-to-end project presents a great learning opportunity for me. 

## The pipeline
I first started off by doing some preliminary understanding of my own requirements. I checked out the 3 websites and identify what information would I like to store and what are the problems I may encounter during the pipeline.

The first problem I would encounter is that the 3 websites are using unlimited scrolling whereby more products are displayed as users scroll to the bottom of the page. This presents a challenge as I couldn't simply use the typical `request` package. Instead, I relied on `selenium` to mimic the scrolling action and I cross referenced a few articles such as this [medium page](https://medium.com/analytics-vidhya/using-python-and-selenium-to-scrape-infinite-scroll-web-pages-825d12c24ec7) by Kuan Wei.

As I did more tests with Jupyter notebook, I started to understand my pipeline and how to foolproof it for future improvement. I would want to save the raw text data from the website upon the end of the page so that I could re-extract the product details in the future once I have improved my data extraction codes.

Thus, I have developed my upstream pipeline by the simple goal of opening the URL, scrolling all the way down to the end of the page and save the raw text data. Of course, I would need to some timestamps such as extraction datetime, creation datetime etc.

## The works
This project also presented me an opportunity to work with AWS especially since I definitely couldn't use my laptop as the server and allow it to run perpetually to collect data. That plus my laptop does not have the resources to run the pipeline full time.

I first have to setup my database. I had gone with AWS RDS MySQL for the first week of development since it is the recommended database to use. However, as I reviewed my cost, I realize that it is quite pricey in the long run as I do not intend to pay over USD$500 per year just to host a database. 

I explored alternatives and found out that I could host my MySQL server on an EC2. Great! Another opportunity to work with EC2 since I would need something to run my scripts to collect the data everyday anyway. Hosting MySQL server on EC2 is definitely costing me way less than AWS RDS especially for my use case.

As I developed and tested my data collection scripts on my local machine, I also had to test out the scripts in the EC2 instances before I deployed the codes to production. The codes are working as expected after I have configured my security group to allow inbound traffic from my local machine and EC2 instances to my MySQL server. 

## The future
I have now productionize the data collection scripts for all 3 supermarkets - NTUC Fairprice, Sheng Siong and Cold Storage since mid Nov 2023. I would have to review the cost again and further optimize my cost since I am aware of the available saving plans.

Besides thatm , my next step is to work on the data extraction scripts as the currated raw text data from each supermarket is slightly different. I would want to extract the product price and amount out since some companies may charge the same price but secretly reduce the amount.

Till next time, cheers and wish me all the best!