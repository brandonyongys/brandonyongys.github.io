---
layout: post
title: Roadmap of RedditSG project on pause
tags: [reddit, singapore, app, roadmap]
comments: true
published: true

date:   2022-11-05
categories: deployment, app-development
---

After over 1.5 months of effort, I came to the realization that I have much to learn. I have overestimated the work needed to make the RedditSG project a success, and there are a lot of solutions to unpack and develop. There is too much to do for a one-man team especially when I need to manage the entire pipeline from data collection to developing and deploying the app. Let me break it down in stages.

In the upstream, I would definitely need to collect the data. Once I have collected the data, I would need to do some preprocessing and store the data appropriately. To store it appropriately, I would have to determine which database is an appropriate database to use and determine the database schema considering that I could extract a lot of information using the [PRAW API](https://praw.readthedocs.io/en/stable/).

In the mid stream, I would need to do some preprocessing on the data so that I could deliver what I hope to (word cloud, sentiment analysis etc.). At this point, I have to admit that I am not as good as I thought I am in processing text data although I have a lot of books here and there. I just need to simplify the work and do more practices especially using smaller dataset.

In the downstream, I would want to pack whatever I have developed into a package and build an app that allows a new user to interactively explore the RedditSG comments while having the flexibility of changing the period. 

In both the up and downstream, I have to learn cloud technology like AWS or GCP so that I could automate the pipeline without having to launch it from my laptop. 

There is just much to learn :( It is disappointing to have to put this project on hold for a while but at least I know where the gaps in my knowledge and skill are.