---
layout: page
title: SG Safety # Project post title
description: Analysis on SG crimes # Project post description
img: https://qph.cf2.quoracdn.net/main-qimg-41e5f3b766414dee38a0f09f0923185f-pjlq
importance: 3
category: descriptive # deployment / predictive / descriptive, if wrong category, the post won't be posted

comments: true
published: false
---

I moved to Singapore back in 2012 to further my studies without knowing much about it. I have only been to Singapore once and that was a 4D3N trip with my friends. I didn't know how expensive the things were, how different Singapore was from Malaysia, and more importantly, how safe it was. It was only after I moved here that I started to learn about all these little things that make Singapore *Singapore*.

Throughout the years, it has been very safe for me. I could cross the road safely, walk late at night with little worries and leave things unattended for a while without being paranoid that it would go missing. However, my perspective of Singapore safety changed when my laundry that was hanging out in the corridor was stolen. Everything including my favourite shirts was missing _or stolen_! I lodged a police report but nothing was achieved. I guess that saying, "Low crime does not mean no crime" is true. Most people are very likely to be taking Singapore's low crime rate for granted.

Given the unfortunate incident, I would like to take a deeper look at Singapore safety over the years, especially since I moved. All the data that I am using here are all obtained from [Data.gov.sg](https://data.gov.sg/), published by the Ministry of Home Affairs - Singapore Police Force. The data was accurate as of 15 Aug 2020.

<hr>

# Total crime in Singapore
In the dataset provided by SPF, the cases were categorized into 6 different categories, which were:
1. Crimes Against Persons,
1. Violent / Serious Property Crimes,
1. Housebreaking And Related Crimes,
1. Theft And Related Crimes,
1. Commercial Crimes,
1. Miscellaneous Crimes.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-sg-crime/Annual%20no%20of%20reported%20cases%20by%20crime%20classification.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


Above figure shows the total annual number of cases as well as the number of cases for each of the 6 categories. 
Firstly, you could observe that the total cases have decreased from almost 37,500 cases in 2005 to about 30k cases in 2013 before rising again to a total of 35k cases in 2019. A huge chunk of the reported cases were theft related cases. Violent/serious property related and housebreaking crimes have declined slowly over the years. From 2005 to 2013, as other categories of crime remain relatively stable, the total annual cases have declined.

However, from 2014 onwards, the number of cases for commercial related crimes have started to rise rapidly as well as crimes against persons and miscellaneous crimes have been rising slowly. These increase has outpaced the decline in the other 3 categories leading to an increase in total crimes.

It is quite daunting to learn that as theft crimes decline, people were commiting another type of crime. Does this mean that Singapore is still equally dangerous as before? 

<hr>

# Crime rate in Singapore
The total crime shows a part of the big picture. When we considered the population growth in Singapore, the numbers didn't seem as daunting anymore.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-sg-crime/Annual%20no%20of%20reported%20cases%20by%20crime%20classification%20per%20100k%20population.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The crime rate has declined from about 900 cases per 100k population in 2005 to 555 in 2013 before increasing and hover about 650 cases per 100k population ever since. Just as before, the initial decline in crime rate are mainly due to decrease in theft crimes. Then, the commercial and miscellaneous crimes started to increase which effectively cancel off the effect from theft crime decline. 

No doubt that we should be thankful that the overall crime rate is relatively stable since 2014. However, the breakdown of crime rate by category shows where SPF may be lacking. SPF would need to up their effort in curbing commercial crimes.

<hr>

# Major offences
Earlier on, we saw that the crime rate per 100k population has been relatively stable despite the rising annual cases since 2013. How many of these annual cases are considered major offences? SPF has kindly shared the dataset indicating the number of cases for the following major offences:

1. Murder
1. Serious Hurt
1. Rape
1. Outrage Of Modesty
1. Rioting
1. Robbery
1. Housebreaking
1. Theft Of Motor Vehicle
1. Snatch Theft
1. Cheating Related Offences

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-sg-crime/Annual%20no%20of%20major%20offences.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The figure above shows the annual number of major offences and also the proportion of the major offences to the total cases reported in each year from 2011 to 2018. The annual number of major offences declined to its lowest at 7,198 cases in 2013 before climbing up ever since. Despite the slight decrease from 2015 to 2016, the general trend is that there are more major offences every year. 

In terms of proportion, the major offences has increased from 25.4% in 2011 to 36.6% in 2018. Both the number and proportion show a very worrying trend as there are more major offences committed each year.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-sg-crime/Annual%20no%20of%20major%20offences%20by%20type.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Most of the major offences are relatively constant throughout the years except cheating related and outrage of modesty offences. Cheating related offences have been on the rise since 2012 where the number of cases more than doubled from 3,419 in 2012 to 9,193 cases in 2018. Such offences include online scam such as sales of goods or services where the seller are no longer contactable after payment is made. 

Another major offence to look out for is outrage of modesty. Though the rise is not as dramatic as that of the cheating related offences, it is still on a rise since 2016. It rose from 1,282 in 2016 to 1,728 in 2018. There could be more in 2019 and 2020 with more incidents happening in universities as these incidents are hitting the headlines.

<hr>

# Preventable offences
SPF has also shared the preventable crimes by NPC. The preventable crimes, as determined by SPF are:
1. Housebreaking
1. Outrage Of Modesty
1. Robbery
1. Snatch Theft
1. Theft Of Motor Vehicle

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202008-sg-crime/Preventable%20crimes%20and%20the%20proportion%20to%20its%20total.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The figures above show the annual number of cases and also the proportion of the preventable cases to its annual cases. You can clearly see that at least 98% of the annual reported cases in each of the 5 major offences can be prevented. 

Despite the decreasing trend in all except for outrage of modesty, this figure itself shows there are still people use are careless in taking care of their own properties. As for outrage of modesty, the annual cases have gone up and SPF has determined that most of them can be prevented. SPF has defined outrage of modesty as molestation ([source](https://www.police.gov.sg/Advisories/Crime/Outrage-of-Modesty)). It could be prevented when the victims are either alone or walking towards a secluded area. However, in a crowded area, it could be more difficult to prevent.


<div class="l-page">
  <iframe src="{{ '/assets/img/202008-sg-crime/sg_crime.html' | relative_url }}" frameborder='0' scrolling='no' height="500px" width="100%" style="border: 1px dashed grey;"></iframe>
</div>

Above is a map of Singapore showing the boundary of each NPC and the colour intensity represents the number of preventable cases in each NPC in 2018. As you can seen, most of the preventable cases happened in the city area such as MBS and Orchard. Such high count of cases happened in area with high traffic flow.

<hr>

# In short
Based on the datasets released by SPF, we can conclude that:
1. The annual reported crimes and crime rate all categories except commercial crimes have generally declined or remained relatively constant over the years. 
1. Commercial crimes have started to rise since 2014 due to online scams. Sellers on platforms such as Carousel are uncontactable once payment has been made.
1. The proportion of major offences in the total offences have increased from 25% in 2011 to 37% in 2018.
1. Almost all housebreaking, outrage of modesty, robbery, snatch theft and vechicle theft can be prevented.

So, the question that I want to answer - **_Is Singapore no longer safe?_** 

The answer is yes and no. The physical Singapore is getting safer as the reported crimes and crime rate are generally decreasing. However, the cyber world of Singapore is getting more dangerous. People are getting more accustomed with technology and more and more activities are done online. Some people have forgotten that the cyber world is still being operated by actual people and there are people trying to steal something from others. Everyone need to be as vigilent online as they would be in the real world. There is only so much SPF could do. They could only apprehend the perpetrator once the crime is committed but not before. 

The incident of my stolen laundry is a very unfortunate incident. Despite the decreasing crime rate, low crime is definitely not no crime. I was being too lax and forgot about that. 