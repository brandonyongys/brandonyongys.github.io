---
layout: post
title: The FIRE Movement
tags: [reddit, finance, fire]
comments: true
published: true

date:   2020-08-16
description: FIRE is financially independent and retire early
categories: analysis
---

A personal interest of mine and also one of the main objectives in my life ins to achieve financial independence. Like how there is a dedicated sub for the Singapore community and people into finance, there is also a dedicated sub for people who are into financial independence. As before, I am going to learn and data mine the weekly "Help me FIRE!" thread on [/r/financialindependence](https://old.reddit.com/r/financialindependence/). In total, I have crawled the comments in the weekly thread dated from 4th March 2019 to 20th July 2020 using the [PRAW API](https://praw.readthedocs.io/en/latest/). The latest pinned thread that started on 27th July 2020 is excluded from my analysis as it has just begun when I first started my analysis. For that 1 year and 5 months worth of data, I have a total of 10,212 comments to work with.

In the weekly thread, the sub moderator has shared some guideline on what to share when asking for help/advice. The posters would typically give a brief introduction such as age, industry and location, and more specific personal finance related details such as FIRE milestones and expenditure breakdown.

<hr>

## First, let's take a look at comments on a high level

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-finance-FIRE/00%20Weekly%20no%20of%20comments.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

First I would want to look at is the number of comments in each weekly thread. There is hardly any growth in terms of number of comments in each weekly thread. There is no obvious upwards or downwards trend. Instead, it is rather stagnant as it would normally fluctuates between 50 to 250 comments with an average of 133 comments. The low comments count in the 1st July 2019 thread is due to lack of questions by others.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-finance-FIRE/03%20Boxplot%20no%20of%20words.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

As for the number of words, the comment is typically 400 words or less, excluding any quotes. The comments with 400 words or more are usually the comments from the people who are seeking for advice, as they are doing their best to provide as much information as needed so that they could get as much advice and help as possible. On the other hand, the comments with 400 words or less are usually the responses to the original poster. 

<hr>

## What is the background of the people who usually ask for help?
Given the information that needed to be shared, I'd try to give some profile from the somewhat structured yet unstructured data. First, I have to clean up my data by removing all the deleted or removed comments. I then removed the quotes within the comments as it can lead me to double count instead. After messing around with regular expression and doing my best, below are some of the profiles I managed to extract.

### Current location
The current country of the users are rather easy to extract. I could easily extract the possible countries of each user by comparing each word within the comment to a list of countries and major cities. Besides that, I also have to compare the words to the list of states in the US. Once I got the possible list of countries, I would extract the country that was mentioned the most, or the first country mentioned if there are 2 modes. I did validate the data by randomly checking 5 weekly threads and found that the distribution from the 5 threads are quite similar to what was found. Based on that, I've plotted the possible current countries of the users as below:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-finance-FIRE/04%20User%20country.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
There are a number of countries where the users are currently at who are in pursue of financial independence. Most of the users who are seeking for FIRE advice are within the United States as it accounts for more than 80% of the seekers. It is not very surprising since Reddit is more US centric and English based forum. So it would be easier to seek advices from people who are in the same country.

When you look at the top 5 countries (US, Canada, UK, Germany and Australia), they are some of the most developed countries in the world. Note that this does not imply that only user from these countries are seeking for financial independence. Rather, there are limited data on users from other countries as there may other websites that are catered more to their financial and economic conditions. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-finance-FIRE/05%20User%20continent%20excluding%20US.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Rather than plotting the number of users in continent, which we all know North America would be the top due to the high counts in US, I plotted a figure by excluding the users from US instead. Besides US, there still a number of users in the Europe and North America outside US who are seeking for advice to achieve their FIRE goals. On top of creating FIRE advice catered to the US, it is worth while to create contents for users from Europe and North America (outside US).

<hr>

### Age group
Extracting the possible age of the users is a more difficult task as there are various numeric values mentioned within the comments. One issue is to identify a possible age number from a dollar and cents number. Another issue is that some users prefer to mention their age group (e.g. 20s or 30s) and others mention their age in various form (e.g. 20M for 20 years old male or 20 years old/yr old/yo). So I relied heavily on regular expression in this section, which I picked up within 1 day and still not an expert in it. Anyway, I have done my best and classified the users into the different age groups.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-finance-FIRE/01%20Age%20distribution.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Most of the users that are seeking for FIRE advice are in their 20s and 30s. This is not too surprising since it would be much easier to achieve their FIRE goals if they were to begin earlier. There are still a group of users who are within their 40s and 50s and are seeking help to FIRE. Although it's not a lot, these older people still need some help as they may be struggling to pay of certain debts or seeking advice on how to speed up their FIRE. I am happy for them to speak up and ask for advice instead continuing down their original path. Better late than never :).

This distribution shows very clearly how financially responsible the younger generations are as they are seeking ways to reduce their financial burden and setting up for their _(future)_ kids. Although there are materials online that the younger generations could have found and read, they may be very much overwhelmed by the vast information and need specific suggestions or opinions instead of a one size fits all solution.

<hr>

## Frequently used terms
Among the thousands of words that are used by the users, I want to find out what are the commonly used 2- and 3-words terms. This can help us to understand what are the usual provided advices. To do this, I have to filter out all the stopwords within the comments. Besides that, I have to remove the URL and also words that don't contribute to our purpose here. After that, I determined the frequently of each term and plotted a wordcloud as below.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-finance-FIRE/06%20Bigram%20for%20all%20comments.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


Based on the bigram word cloud, the top three bigrams are student loan, Roth IRA, and emergency fund. It makes sense to see student loan as one of the most frequently mentioned bigram considering that most of the users who are seeking for FIRE advice are in their 20s. So they would more likely to have some student loan to pay off, especially in the US since their tuition fee is considerably high, and they are adviced to pay it off as soon as possible to reduce their debt. 

In order to achieve FIRE with little worry, one would always need to have an emergency fund for unplanned events such as car repair or unemployment during a crisis. That way, one does not have to be too worried about their day to day living expenses. The emergency fund should be placed in some high yield saving account, a term that is frequently shown in the trigram word cloud below.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-finance-FIRE/06%20Trigram%20for%20all%20comments.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Roth IRA is another frequently mentioned bigram. When we look at the trigram word cloud, we can see that there are a lot of trigrams involving the term Roth IRA. The reason why this is mentioned so frequently is because of the high tax rate in the US despite it being a progressive tax rate. The Americans have to find ways to reduce their tax rate _legally_, especially when they are high earners, and that is by contributing to their Roth IRA. 

In Singapore, our equivalent of Roth IRA is our Supplementary Retirement Scheme (SRS). Similar to the Roth IRA, our contribution to SRS provides us some form of tax relief though there is a cap to the yearly contribution. The SRS contributions can be used to invest in local financial securities such as equities and ETFs. However, unlike the US, there is no capital gain tax.

Another term that is mentioned in the trigram word cloud is the US's 401k plan. US employees can make contributions to their 401k accounts through automatic payroll withholding, and their employers can match some or all of those contributions. The equivalent form for us in the Singapore is our Central Provident Fund (CPF). Different from the US's 401k plan, the employer is required to contribute to our CPF as well, up to 17% of our salary. 

<hr>

## Conclusion

Firstly, we can conclude that the number of comments to the weekly thread is stationary as it would fluctuates between 0 to 300 comments and there is no seasonality observed. The comments can be divided into two groups: 

1. the comments by the original poster seeking for advice by providing details would normally have 400 words or more, and 
1. the responses to such comments offering suggestions and advices with 400 words or less. 

Based on the mined profile of the advice seekers, they are usually in their 20's or 30's and are generally from the US (given that Reddit is US centric). There are advice seekers from all over the world but they are mainly from developed countries such as UK, Canada and Australia. 

The advices that are offered to the US based users typically revolves around the same issues - debt management and Roth IRA. Conceptually, both are talking about the management of some sort rates (interest rate in the former and tax rate in the latter). So the goal would be to minimize such rates by minimizing your debt and maximizing your Roth IRA. In Singapore, our equivalent of Roth IRA is the SRS. Just like Roth IRA, our contributions can be used to reduce our tax rate and it can also be used for investment in the local stock market. 