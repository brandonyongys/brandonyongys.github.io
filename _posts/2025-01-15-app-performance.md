---
layout: post
title: Improving my application performance
# description: What have I done successfully and failed to do?
date: 2025-01-15
tags: [career, technical, programming]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']


comments: true
published: true
---
I have developed multiple applications for both patients facing and internal facing. Recently I have received feedback that one of my internal facing applications is taking a long time to process before returning a payload. As a result, the staff could not make a proper decision at the point of patient care. 

The application in question is a tool to support clinical decision for patient care. It is a tool to automate the targets calculation for the patient based on medical history. Thankfully the app is still under beta testing and the staff are able to determine whether the tool is functioning as expected.

After investigation, I found that there are 2 main issues. The first is that the main endpoint is calling multiple endpoints to query the necessary data from the database before preprocessing. The multiple endpoints call has increased the latency as each call would need to make a round trip before querying the database. To rectify this, I had to refactor the codes and make the database query callable by the endpoint directly instead. 

The second issue is that the app is triggered when the staff visits the patient's profile page. If the same page is visited multiple times - be it by refreshing it, visited by same or different staff throughout the day, the same endpoint is triggered again and again. This can increase the database load and that is not ideal. To combat this, I've set up a caching system and cache the data instead.

These 2 actions should improve the overall performance of the application. I will have to continue monitoring it.