---
layout: post
title: Analysis of SGReddit Daily Thread - Part 2
tags: [reddit, singapore]
comments: true
published: true
---

In this section, I have to say that there isn't much analysis as much as I am curious about certain things. First, I am curious how many upvotes does a typical comment received and what are some of the interesting most upvoted and downvoted comments of all times. Besides that, what are some of the commonly used words by the community.

<hr>

### Distribution of votes received
Here I have plotted the distribution of the votes received for each comment by month using a letter-value plot from 2017 to 2020 only. The letter-value plot is an enhanced version of a boxplot and it is capable of displaying the tail portion of the distribution that covers the extreme values. A distribution plot would not have displayed the extreme values that are deemed to be outliers and a normal boxplot would have labelled many of the extreme values as outliers.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202017.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202018.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202019.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202020.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

From the above four figures, you can see that the typical range of votes received for a comment would be between -10 to 40 in 2017 and would gradually change to -15 to 30 in 2020. The median would still remain the same at about 1-5 votes. Besides that, that maximum votes received also slowly decline from 140 to the current level of 80. The typical lowest votes received is still relatively constant at about -40.

Based on the extend of the votes distribution, you may conclude that SG users would much rather give an upvote to good comments that they like rather than to give a downvote to a comment that they may not like or disagree.

<hr>

### What are some of the best and worst comments?
You may be wondering what are some of the best and worst comments by votes? Below are some of the interesting best and worst comments over the years.

#### _Best comments_

> My Golden Retriever usually welcomes the people she likes home by helping to carry your bag or grocery bags, any letters or folders in your hands, etc. Just got home from school but had nothing for her to carry, so she grabbed my left shoe and tried to bring it into the house. When I told her I had nothing for her, she grabbed my right shoe. I took it back and placed it outside, she grabbed another pair of shoe I had outside. Told her "Don't do that!", she went out to look for my socks to bring in. 
> 
> This girl... 😂 Can't bear to scold her for trying to be helpful so I just sayang her. Her tail wag until like helicopter. 
> 
> Edit: postman just came by. here she is doing her job like a good girl http://imgur.com/a/cvxWa
>
> by: _unknown user_ (136 votes)


<blockquote>
So theres this female colleague who is around 30 plus years old. She constantly tries to talk shit about me in front of the boss, e.g. he always never do this.... he anyhow how out this here.... how come he always like that...

When we have lunch together with the boss, she will do her irritating fake ass laugh whenever the boss say something while I just sit there quietly eat my food and use my phone. Dont even know what she trying to do but always laughing and acting that she v interested in the convo. Heng I intern and gonna leave end of the month, dont need see her anymore.

One more thing, she doesnt know I'm the boss' son. Bitch 

by: _dragonbad30_ (116 votes)
</blockquote>

<blockquote>
LIVE: This auntie KPKB this younger guy for sitting on the priority seat. The younger guy just stands up and ripped off his prosthetic leg. The auntie died of embarrassment.

UPDATE: Auntie mumble about giving old people sit first...she older.

by: _leo-g_ (106 votes)
</blockquote>
<hr>

#### _Worst comments_

<blockquote>
Yesterday, girlfriend and I created a Tinder account and lured a couple of guys to Esplanade to meet up. They were really horny and dtf. The look on their faces when we made them go in circles and finally unmatch them is priceless. Sorry we had so much free time!

Then there was this Jewish guy who wanted to meet up at Marina Mandarin and found out it was a prank. He identified us pretty quickly and walked towards our hiding spot. We ran and luckily there was a taxi nearby. That adrenaline rush tho. 5/7 would do it again!

by: _statelesspirate_ (-81 votes)

</blockquote>

<blockquote>
Speedpost just dump my parcel on my shoe rack and no updates on the delivery status online. Can I report the parcel as lost and get the seller to send/refund me?

by: _Siobak118_ (-43 votes)
</blockquote>
<blockquote>
Did Malaysia fuck us over by closing their borders and was it the right move for them to make?

by: _Afraidofdownvotes0_ (-31 votes)
</blockquote>

Based on these few examples, we can see that some of the best comments make the readers feel good and amused whereas the worst comments are usually reflect immmature thinking or dishonesty. 
<hr>

### What are some of the commonly used words?
This is my very first noob attempt at determining the commonly user words in sg reddit. I have to say that this is a very low effort, low return section as I am still learning how to do a proper text analysis. 

I've plotted a word cloud for the entire year of 2019 as well as for the circuit breaker period. Prior to analysis, I have removed most of the commonly stopwords and removed more words that do not bring much significance.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Word%20frequency%20for%20year%202019.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Word%20frequency%20for%20CB%20duration.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Here, you can see what are some of the most frequently used words by the users. The top few words that are consistently used are "one", "think" and"work". Of course, the above analysis is still in progress, as I did not remove all the stopwords nor have I removed any emoji or url. 

That's all for this part 2. It's quite a short section. In the next section, I'd like to dive further in and see how have the discussion topics changed over the years.
