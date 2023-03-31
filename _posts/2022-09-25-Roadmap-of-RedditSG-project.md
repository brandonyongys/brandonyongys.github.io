---
layout: post
title: Roadmap of RedditSG project
tags: [reddit, singapore, app, roadmap]
comments: true
published: false

date:   2022-09-25
categories: deployment, app-development
---

I have always wanted to work on my personal project - mining, analysing and developing a model for the daily SG thread on [Singapore subreddit](https://old.reddit.com/r/singapore/) all these while. I have been procrastinating on it for over 2 years since I posted the part 1, 2 and 3 of my daily SG thread analysis.

On top of simply mining, analysing and developing a model, I do hope to eventually deploy an app on a platform especially since I deployed a dashboard on Heroku to illustrate the status of the different hawker centres across Singapore. Though it is sad that Heroku is no longer offering a [free service](https://devcenter.heroku.com/articles/free-dyno-hours) soon and my dashboard would no longer be available, I would have to search for an alternative platform to deploy my eventual RedditSG app.

Moreover, I have finally started on my natural language processing (NLP) journey back in June 2022 (after procrastinating a few years again!) by attending the free [CS224n: Natural Language Processing with Deep Learning course](http://web.stanford.edu/class/cs224n/) by Stanfard University and also started reading the [Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/) book by Dan Jurafsky and James H. Martin, after being motivated by my team's external advisor at SGH.

Now with the much accumulated knowledge (and still growing), I am now more confident in my skills as a data scientist and more motivated than ever to work on my personal project, though it may not have any signficant values at the moment. The developed skills and knowledge are nonetheless valuable.

Now, I feel more confident about doing my own personal project. The current personal project I am focusing on right now is to develop an app that automatically extracts the latest comments of the daily SG thread before conducting some analysis and updating a model.

The plan is as follows:
1) Develop a script to automatically extract and update the latest comments
2) Develop a word cloud of the daily thread based on the selected date range or date. 
	The word cloud should be updated automatically based on the selected date range or date.
3) Develop a cluster analysis to see how the different comments are similar or different, and identify the topics of interest
4) Develop a language model that predicts the next words based on the given words - could be simple n-gram model or neural language model.
5) If time permits, I would want to analyse how the different users are connected based on the subreddits they post in or interested in. Some sort of network analysis.
6) If all goes well, all these should be packaged into an app and deployed somewhere - probably Amazon Web Services if appropriate.
