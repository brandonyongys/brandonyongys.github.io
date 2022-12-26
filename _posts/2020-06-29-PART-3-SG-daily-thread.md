---
layout: post
title: Analysis of SGReddit Daily Thread - Part 3
tags: [reddit, singapore]
comments: true
published: true

date:   2020-06-29
description: Part of 3 of 3-parts analysis of SGReddit daily threads
categories: analysis
---

This will be my first attempt to do a proper text analysis. In this part, I am going to determine the most frequent bigram and trigram, that is the most frequently used two-word and three-word terms. The bigram and trigram are then plotted into a word cloud, as shown in the previous section. This section is particularly difficult because there are a number of things that I have to do first before I can finally determine the most frequent bigram and trigram.

First, there are modern slangs that I have to replace with such as "gonna" to "going to" and "wanna" to "want to". These slangs have to be replaced first or else these words would be lemmatized into two separate words, which will affect the word cloud. Second, there are a number of url that need to be removed. 

The challenging part of the preprocessing step is removing the emoji. I have searched online and used a lot of the suggested emoji removal step and it's not 100% successful. Despite that, I still manage to remove most of it and left a few emoji that may skew the results in the end a little bit. But I'll take that as a success for a first attempt.

<hr>

### Text analysis for year 2019
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Most%20frequently%20occurring%20bigrams%20connected%20with%20an%20underscore_%20for%20comments%20in%20year%202019.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Above is the word cloud for the most frequently used bigram terms for year 2019. It may seems like a bunch of random bigrams but you can see what are the terms that users on SG reddit likes to use. Somehow, they prefer to use bigram that ends with "like" such as "feel like", "sound like", "look like" etc. Besides that, you can see what food that are commonly mentioned such as cai png (mixed rice), chicken rice and ice cream. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Most%20frequently%20occurring%20trigrams%20connected%20with%20an%20underscore_%20for%20comments%20in%20year%202019.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Here, I have plotted the trigram for 2019. Trigram seems to be more useful as it provides terms that are more informative. As mentioned previously, I have tried my best to remove all the emoji and managed to do some for most of it. There are a few left behind, which explains why there are weird trigrams.

Anyway, based on the word cloud, the users tend to talk about jobs, both full time and part time job, but part time job is more popular. This is an indicative that either the communmity comprises of young adults who are looking for part time jobs or adults that are looking for some part time job on top of their full time job.

Another popular term is to wish someone to get well soon or feel better soon. This shows that when people are sick, they tend to be online and share with the world that they are sick. Besides wishing someone to get well soon, the community also tend to wish "happy birthday" or "happy cake day", which is the day the reddit account was created, quite frequently.

There are a few food that are mentioned frequently too such as cai png, yong tau foo, char kway teow and bak chor mee. On top of that, there are a few places that are mentioned often such as far east plaza and and mo kio. 

<hr>

### Text analysis for CB period
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Most%20frequently%20occurring%20bigrams%20connected%20with%20an%20underscore_%20for%20comments%20during%20CB.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
Generally the bigrams are similar to that of 2019. But you can see a few new terms related to the current Covid-19 pandemic have popped out such as essential service, wear mask and video call. Mental health was mentioned a number of times. This could be because with CB, mental health services were considered as non-essential despite it being a medical service. This sparked a debate as to why it was classified so.

The recently released game, Animal Crossing, was mentioned quite often and the release of the game coincide nicely with the start of circuit breaker. With the CB, this gives the user more time to play Animal Crossing as they would spending more time at home, be it working or studying. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Most%20frequently%20occurring%20trigrams%20connected%20with%20an%20underscore_%20for%20comments%20during%20CB.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Based on the trigram word cloud, there are indication of users asking others to contact them for talk such as feel free dm, dm talk anything and free dm talk. This is an indication that the community is starting to feel isolated and lonely during the circuit breaker despite spending more time at home with their family. They may need a form of break from their family. Or this is an indication that they are trying to help patients who need the mental health services but couldn't get. 

Another term that's popular is work permit holder. This is very likely due to the outbreak of Covid-19 in the migrant worker dormitory. Back then there was a sudden and explosive counts of confirmed cases, reaching up to 1000 and more for a period of time. This sparked a debate and discussion online. After almost 2 months, the counts have gone down.

This is the end of my analysis of the SGreddit. It may not have been a long and comprehensive analysis, but hey, I've learned a lot of things here and there. 
