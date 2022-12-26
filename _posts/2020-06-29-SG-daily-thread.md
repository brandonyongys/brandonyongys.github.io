---
layout: post
title: SGReddit, how are you?
tags: [reddit, singapore]
comments: true
published: false

date:   2020-06-29
description: Is this a summary of the 3 parts series?
categories: analysis
---


[Reddit](https://www.reddit.com/) is a very popular website which I frequent almost on a daily basis. That is how I mostly keep up to date with the daily news. There are subforums, called subreddit, which are dedicated to various communities such as [world news](https://www.reddit.com/r/worldnews/), [data science](https://www.reddit.com/r/datascience/) and [skin care addiction](ttps://www.reddit.com/r/SkincareAddiction/). One particular sub that I often visit is the [SGreddit](https://www.reddit.com/singapore/), where I find out the latest memes or happenings in Singapore. Now, just like every other sub, there is a pinned daily thread that allows the users to write comments about anything that don't warrant a separate thread and it is called the "/r/singapore random discussion and small questions thread". I'm interested to analyse the daily thread right from the beginning until now and try to find some insights of the SGreddit, especially during this circuit breaker period where people are either working from home or having home-based learning.

The daily threads are scraped using the [PRAW API](https://praw.readthedocs.io/en/latest/) from 24th June 2014 up to 2nd June 2020. With that, I have managed to mine a total of 2166 out of 2173 threads. 7 threads are missing and cannot be found on Reddit. No idea why is that the case. The information that I mined are:
1. content of the comment  
1. username of the comment
1. time of comment submission
1. votes of the comment

The additional information that I extracted are the day of the week and week number of when the comments were submitted. Once preprocessed, all these data are stored as a csv file though there may be better ways to store the text data such as in a json file. In my analysis, I ignore comments that were either deleted or removed as I would not be able to do any analysis of the text except for the timestamp data.


### How has the community of SG daily thread grown over the years?
First thing I want to know is how has the community grown over the years, even before I joined Reddit. One way to track and estimate the growth of the community is to determine the number of daily unique users for the daily thread. No doubt that a person may have created multiple accounts such as a throwaway account and make a comment on the daily thread but based on my experience, I don't see as many throwaway accounts. So this should be a good representation of the community growth.

![No of daily unique posters](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202006-sg-reddit/No%20of%20unique%20users%20-%20day.png)

Above figure is the number of daily unique users for each of the daily thread in a heatmap form. The horizontal axis is the week number of the year and vertical axis is the day of the week with Monday at the top and Sunday at the bottom. As the number of unique users increases, the intensity of the colour increases based on the colour map on the side, starting from light green up to dark green. The white bars in the heatmap represent the missing data. 

Despite the missing data, you can clearly see that the week on week number of unique users have been increasing. Besides that, you can see the clear distinction in the number of unique users on weekday daily threads versus the weekend daily threads. This shows that on weekdays, more redditors would be online due to reasons such as being at work, whereas on weekends, redditors would be doing more work offline such as going out to the shopping malls or exercising.

![No of monthly unique posters](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20unique%20users%20-%20month%202.png?raw=true)

Besides that, I also plotted the total monthly unique users as shown in the figure above. The horizontal axis represents the year and the vertical axis is the month. The total number of unique users for June 2014 and June 2020 are underrepresented as I do not have the full month data. Looking at this figure, you can see that from June 2014 to December 2017, the monthly total unique posters keeps increasing. Starting from January 2018, the monthly total unique posters hovers between 1600 and 1800 and have been that way ever since. 

However, from March 2020, there has been a spike in total monthly unique users and it reaches its peak of 2152 unique users in April 2020. This is due to the Covid-19 pandemic that has caused a great impact on the world. Singapore government has encouraged employers to allow employees to work from home whenever possible. On 7 April 2020, circuit breaker was implemented and all non-essential workers were to work from home and all schools were closed. 



### How has the comments on SG daily thread grown over the years?
Since there is evidence that the community is growing, how about the number of comments made? Are the community becoming more engaged and chattier?

![No of daily posts](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20posts%20-%20day.png?raw=true)

I have plotted another heatmap for the daily number of comments for each of the daily thread. Likewise, the horizontal axis is the week number of the year and the vertical axis is the day of the week. The colour map is centered about 1000 comments.

You can see a progression of the daily number of posts from a very low value of about 50 to about 1000 posts. There is a very clear separation at the start of 2017, that's when the daily posts approach 1000 posts and start to hover around that value since. However, there was a brief period of time in 2018 for approximately 4 weeks that the daily number of posts reached a very high count of 2000 or more posts. The maximum number of posts back then was about 3281.

Besides that, you can also clearly see that the number of posts on the daily threads during the weekend versus the weekdays is vastly different. During the weekdays, the number of posts hover about 1000 posts for the past 3 years. On the other hand, the number of posts would hover about 600 posts. This can be explained simply because of the reduced number of unique users on the weekends, and hence, reduced engagement.

![Median daily posts](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20posts%20-%20day%20median.png?raw=true)

We can take a look from a different perspective by plotting the median number of posts for each day of the week by year. I decided to use the median value instead of mean value because of the high count of comments in 2018, which can significantly skew the results. The values for first 3 years (2014 to 2016) should be taken with a pinch of salt as the number of comments back then was still experiencing growth and hasn't reached its stationary stage yet. So simply taking a median value for then period is like taking the mid point of an ever increasing growth.

However, we can take a look at the data since 2017. The median value of each day of the week is rather consistent. The data for 2018 is the highest simply because of the outliers in early 2018 as mentioned previously. Looking at the data for 2020, the median number of posts is still about the same value as the previous year despite the implemented circuit breaker. _Could this mean that the number of posts per user has dropped?_



### Have the users been posting more?
I am wondering and checking whether has an average user submitting fewer comments. Here, I calculated the average comments per user by dividing the total comments by the total unique users for each day. Then, I plotted another heatmap to illustrate the average number of comments per user since 2014, as shown below. The colour map is centered about the value 3.

![Daily posts per user](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20posts%20per%20user%20-%20day.png?raw=true)

The average number of posts per user back then was about 2 to 3 posts and it has grow up to 3 to 4 posts in recent time. Occasionally the number of posts per user does go up to 5 and beyond. You can see a clear difference in number of posts per user on weekdays versus weekends. Users tend to post about 3 to 4 posts on weekdays and on weekends, they tend to post about 2 to 3. The average user is slightly less chatty because of the reduced number of users that contribute the community engagement.

Looking at the blue bars, which indicate a high number of posts per user, there are two period of time where this happened. First was in end of 2014 and another was in early to mid 2018. In 2014, the users were probably excited about clearing their leaves and school year was going to end, so it was time for them to go on holiday or enjoy their down time. In 2018 though, it was a peculiar period. As indicated previously, this period of time experienced a high number of posts and a high number of users. So this prompts a question - _what was happening back then that caused such a surge in activity?_ 

![Median daily posts per user](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Median%20no%20of%20posts%20per%20user%20-%20day.png?raw=true)

Looking at the heatmap above, the average user in 2020 has posted slightly fewer comments as compared to the median posts per user in 2017 to 2019. This is odd as I would have expected that circuit breaker would have increased the number of users and posts. I suppose that since non-essential workers were working from home for the entire circuit breaker and students were doing home based learning in the first half of circuit breaker and then they were on their June holiday in the second half, so their lives were less happening and they have fewer things to rant or talk about. 



### What about the hourly activity of the daily thread?
I decided to use the data for 2019 to calculate and plot the average hourly number of posts for each day of the week. The reason I chose 2019 data is because there doesn't seem to have any outlier data and also because it is the most recent full year data that I have. 

![Hourly posts](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Hourly%20posts%20-%20average%202019.png?raw=true)
You can clearly is that there is an obvious trend regardless of the day of the week. From 6am all the way to 1pm, the number of comments posted is on a downhill trend. Starting from 1pm, the number of posts start to pick up. This is where the trend of weekday and weekend start to diverge. The reason for the sudden drop in activity from 6am to 1pm is because 1) a new daily thread is posted and pinned, replacing the previous day thread and ending all discussions in the previous day thread, and 2) the users are preparing to go to work/school and are focusing on them first.

On weekdays, the number of comments posted would climb faster than it would on a weekend and it would reach it maximum at about 6-7pm. From there, it would very slowly decrease all the way to 6am. Then the cycle repeats. 

The trend for the weekend is a little bit tricky to see. You would have to look at the end from 1pm of either Saturday or Sunday and connect the trend to the following day (Sunday or Monday) to see the actual trend and to ensure continuity. The number of posted comments on the weekend pick up slower and reach it peak at about 9pm. Then it would go down a little bit and from midnight onwards, it would go up to about 50 comments per hour at 6am before it goes downhill again.  

One thing to note is that on Thursday between 4 to 7pm, the number of comments posted for each hour of the 3 hours time frame is significantly higher than the usual count for a weekday (70 comments vs 60 comments respectively). _Is this because everyone is excited about TGIF the following day?_

![Hourly posts during CB](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Hourly%20posts%20-%20average%20CB.png?raw=true)
I've also plotted the average hourly comments for the ciruit breaker period as well. The shape is generally the same as last year's average hourly comments. However, there are a few notable changes.

The first difference is that there is almost no difference between weekdays and weekend comments especially in the first half of the day. Between 12 to 6am, there was a maximum difference of 20-30 comments for weekday versus weekend comments and it would slowly converge to about 50 comments at 6am. However, during the ciruit breaker, there is almost no difference. The second half of the day, there is still some difference but the difference between weekday and weekend comments are about 10 comments for each hour compared to last year's difference of about 20 comments.

The second difference is that the maximum hourly comments in the first half of the day tend to be lower than the second half of the day. However, that trend is no longer valid as the maximum for the first half and second half are the same, which is about 80 comments. 

Although the hourly comments at 6am is still about 50 comments, the decline in hourly comments have significantly slowed down. For example, in last year's trend, the hourly comments at 8am was about 20 comments but during the circuit breaker period, the comments posted at 8am was nearly double of that (approximately 40 comments).

Another difference is the night activity would slowly die down after a certain hour last year. During circuit breaker, the hourly activity at night didn't die down. Rather, it was stable and sometimes would increase.

All these differences show that circuit breaker has indeed changed the behaviour of the sg redditors. As they couldn't go out and enjoy activities such as dating and shopping, more redditors have spent more time online and engaged with others within the community although the average redditor has posted fewer comments.









In this section, I have to say that there isn't much analysis as much as I am curious about certain things. First, I am curious how many upvotes does a typical comment received and what are some of the interesting most upvoted and downvoted comments of all times. Besides that, what are some of the commonly used words by the community.

### Distribution of votes received
Here I have plotted the distribution of the votes received for each comment by month using a letter-value plot from 2017 to 2020 only. The letter-value plot is an enhanced version of a boxplot and it is capable of displaying the tail portion of the distribution that covers the extreme values. A distribution plot would not have displayed the extreme values that are deemed to be outliers and a normal boxplot would have labelled many of the extreme values as outliers.

![Distribution of votes - 2017](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202017.png?raw=true)
![Distribution of votes - 2018](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202018.png?raw=true)
![Distribution of votes - 2019](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202019.png?raw=true)
![Distribution of votes - 2020](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202020.png?raw=true)

From the above four figures, you can see that the typical range of votes received for a comment would be between -10 to 40 in 2017 and would gradually change to -15 to 30 in 2020. The median would still remain the same at about 1-5 votes. Besides that, that maximum votes received also slowly decline from 140 to the current level of 80. The typical lowest votes received is still relatively constant at about -40.

Based on the extend of the votes distribution, you may conclude that SG users would much rather give an upvote to good comments that they like rather than to give a downvote to a comment that they may not like or disagree.

### What are some of the best and worst comments?
You may be wondering what are some of the best and worst comments by votes? Below are some of the interesting best and worst comments over the years.

#### _Best comments_
> My Golden Retriever usually welcomes the people she likes home by helping to carry your bag or grocery bags, any letters or folders in your hands, etc. Just got home from school but had nothing for her to carry, so she grabbed my left shoe and tried to bring it into the house. When I told her I had nothing for her, she grabbed my right shoe. I took it back and placed it outside, she grabbed another pair of shoe I had outside. Told her "Don't do that!", she went out to look for my socks to bring in. 
>
> This girl... 😂 Can't bear to scold her for trying to be helpful so I just sayang her. Her tail wag until like helicopter. 
>
>Edit: postman just came by. here she is doing her job like a good girl http://imgur.com/a/cvxWa

by: _unknown user_ (136 votes)


>So theres this female colleague who is around 30 plus years old. She constantly tries to talk shit about me in front of the boss, e.g. he always never do this.... he anyhow how out this here.... how come he always like that...
>
>When we have lunch together with the boss, she will do her irritating fake ass laugh whenever the boss say something while I just sit there quietly eat my food and use my phone. Dont even know what she trying to do but always laughing and acting that she v interested in the convo. Heng I intern and gonna leave end of the month, dont need see her anymore.
>
>One more thing, she doesnt know I'm the boss' son. Bitch 

by: _dragonbad30_ (116 votes)

>LIVE: This auntie KPKB this younger guy for sitting on the priority seat. The younger guy just stands up and ripped off his prosthetic leg. The auntie died of embarrassment.
>
>UPDATE: Auntie mumble about giving old people sit first...she older.

by: _leo-g_ (106 votes)

#### _Worst comments_

>Yesterday, girlfriend and I created a Tinder account and lured a couple of guys to Esplanade to meet up. They were really horny and dtf. The look on their faces when we made them go in circles and finally unmatch them is priceless. Sorry we had so much free time!
>
>Then there was this Jewish guy who wanted to meet up at Marina Mandarin and found out it was a prank. He identified us pretty quickly and walked towards our hiding spot. We ran and luckily there was a taxi nearby. That adrenaline rush tho. 5/7 would do it again!

by: _statelesspirate_ (-81 votes)

> Speedpost just dump my parcel on my shoe rack and no updates on the delivery status online. Can I report the parcel as lost and get the seller to send/refund me?

by: _Siobak118_ (-43 votes)

> Did Malaysia fuck us over by closing their borders and was it the right move for them to make?

by: _Afraidofdownvotes0_ (-31 votes)


Based on these few examples, we can see that some of the best comments make the readers feel good and amused whereas the worst comments are usually reflect immmature thinking or dishonesty. 

### What are some of the commonly used words?
This is my very first attempt at determining the commonly user words in SGreddit. I have removed most of the stopwords and also words that do not bring significant meaning. The removal of words is a very iterative process where I am constantly removing words after plotting a word cloud. In the end, I have tried my best to clean the text data and generate some insights into the discussions.

Some of the challenges I face with dealing with the text data (comments especially) is the use of emoji. Simple emojis such as :) and :( are removed easily but there are other emojis that represented differently. Despite the difficulty, I have managed to remove most of it and left a few emojis which may skew the results. BUT I'll still take it as a success considering it is my first attempt.

#### Text analysis for year 2019
![Bigram for 2019](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Most%20frequently%20occurring%20bigrams%20connected%20with%20an%20underscore_%20for%20comments%20in%20year%202019.png?raw=true)
Above is the word cloud for the most frequently used bigram terms for year 2019. It may seems like a bunch of random bigrams but you can see what are the terms that users on SG reddit likes to use. Somehow, they prefer to use bigram that ends with "like" such as "feel like", "sound like", "look like" etc. Besides that, you can see what food that are commonly mentioned such as cai png (mixed rice), chicken rice and ice cream. 

![Trigram for 2019](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Most%20frequently%20occurring%20trigrams%20connected%20with%20an%20underscore_%20for%20comments%20in%20year%202019.png?raw=true)

Here, I have plotted the trigram for 2019. Trigram seems to be more useful as it provides terms that are more informative. As mentioned previously, I have tried my best to remove all the emoji and managed to do some for most of it. There are a few left behind, which explains why there are weird trigrams.

Anyway, based on the word cloud, the users tend to talk about jobs, both full time and part time job, but part time job is more popular. This is an indicative that either the communmity comprises of young adults who are looking for part time jobs or adults that are looking for some part time job on top of their full time job. This raises a question - **_are people in Singapore earning enough for their daily expenses and retirement or are they spending more than they are earning?_**

Another popular term is to wish someone to get well soon or feel better soon. This shows that when people are sick, they tend to be online and share with the world that they are sick. Besides wishing someone to get well soon, the community also tend to wish "happy birthday" or "happy cake day", which is the day the reddit account was created, quite frequently.

There are a few food that are mentioned frequently too such as cai png, yong tau foo, char kway teow and bak chor mee. On top of that, there are a few places that are mentioned often such as far east plaza and and mo kio. 


#### Text analysis for CB period
![Bigram for CB](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Most%20frequently%20occurring%20bigrams%20connected%20with%20an%20underscore_%20for%20comments%20during%20CB.png?raw=true)
Generally the bigrams are similar to that of 2019. But you can see a few new terms related to the current Covid-19 pandemic have popped out such as essential service, wear mask and video call. Mental health was mentioned a number of times. This could be because with CB, mental health services were considered as non-essential despite it being a medical service. This sparked a debate as to why it was classified so.

The recently released game, Animal Crossing, was mentioned quite often and the release of the game coincide nicely with the start of circuit breaker. With the CB, this gives the user more time to play Animal Crossing as they would spending more time at home, be it working or studying. 

![Trigram for CB](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Most%20frequently%20occurring%20trigrams%20connected%20with%20an%20underscore_%20for%20comments%20during%20CB.png?raw=true)

Based on the trigram word cloud, there are indication of users asking others to contact them for talk such as feel free dm, dm talk anything and free dm talk. This is an indication that the community is starting to feel isolated and lonely during the circuit breaker despite spending more time at home with their family. They may need a form of break from their family. Or this is an indication that they are trying to help patients who need the mental health services but couldn't get. 

Another term that's popular is work permit holder. This is very likely due to the outbreak of Covid-19 in the migrant worker dormitories. Back then there was a sudden and explosive counts of confirmed cases, reaching up to 1000 and more for a period of time. This sparked a debate and discussion online. After almost 2 months, the counts have gone down.

#### In short
The community of SGreddit has grown since 2014 but the growth has slowed down significantly since 2018 where the total monthly users hover between 1600 and 1800. With the ongoing circuit breaker, the community has become more active with more users logging in. This is due to the extra time everyone studying/working at home. It has come to the point where people are more active than ever especially at night. However, despite the additional activity, some of the users may actually feel more isolated, depressed or lonely during the circuit breaker and feel the need to reach out to others to talk. The recent outbreak in migrant worker dormitories has sparked an online discussion.