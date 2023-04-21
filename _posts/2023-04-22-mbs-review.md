---
date: 2023-04-22

layout: post
title: How well perceived is Marina Bay Sands?
description: Sentiment analysis of MBS reviews

# if post 
# tags: [test]
# categories: sample-posts # if post

comments: true
published: true

---

Marina Bay Sands, or otherwise known as MBS, is an iconic integrated resort in Singapore and it is a landmark that could not be missed when one visits Singapore. It opened back in mid 2010 and has been operating since. I myself have visited MBS once in a while and have had the opportunity to stay there a few times with a balcony view facing the city business district or the iconic Gardens by the Bay. 

Throughout my few stays, I have enjoyed myself very much and would like to find out how do the other guests find them. I happened to find the collated reviews from Tripadvisor.com on [Kaggle](https://www.kaggle.com/datasets/lucashkliu/marina-bay-sands-hotel-reviews-on-tripadvisor), which has 10,232 reviews. 

<hr>

# Rating reviews
<iframe width="1000" height="250" frameborder="0" scrolling="yes" src="/assets/img/202304-mbs_reviews/avg_rating_over_time.html"></iframe>

The number of MBS reviews was rather low in 2014 as the number of reviews was below 100. However, it started to hover above 100 from the start of 2015 to April 2019 with the exception of second quarter of 2017. Since then, the number of reviews have declined in a downward trend and nearly hit 0 in April 2020 when Circuit Breaker was announced by the Singapore Government. The number of reviews have hovered below up till October 2022. 

Despite that, the average monthly rating of MBS has remained relatively consistent at 4.2-4.5 from Apr 2014 up to Covid-19 pandemic. Thereafter, the average rating has rather haphazard, ranging from 4 to 5, due to the low count of reviews.

<hr>

# Sentiment analysis
Although the rating entered by the guest is useful to have an indicator of how good the hotel is, it is not an easy feat to know how does the guest actually feel about their stay, unless one spends time to read all the reviews. To do that, I applied 3 different pre-trained models from [Hugging Face](https://huggingface.co/), which are:
* [SiEBERT](https://huggingface.co/siebert/sentiment-roberta-large-english) - to generate positive and negative sentiments.
* [TweetEval](https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment) - to generate positive, negative **and** neutral sentiments.
* [Emotion English DistilRoBERTa-base](https://huggingface.co/j-hartmann/emotion-english-distilroberta-base) - to generate the emotion from the reviews.

<iframe width="1000" height="250" frameborder="0" scrolling="yes" src="/assets/img/202304-mbs_reviews/model2_SA.html"></iframe>
<iframe width="1000" height="250" frameborder="0" scrolling="yes" src="/assets/img/202304-mbs_reviews/model1_SA.html"></iframe>

According to TweetEval and SiEBERT, the reviews are generally 80% positive, which are consistent with the earlier simple rating analysis. However, this result should be taken with a pinch of salt as the two models are not fine-tuned to evaluate reviews though SiEBERT is more robust as it has been tuned to various datasets.

<iframe width="1000" height="250" frameborder="0" scrolling="yes" src="/assets/img/202304-mbs_reviews/model3_SA.html"></iframe>

The emotion analysis by the 3rd model is more informative. The reviews are generally positive as indicated by the reviews labelled as "Joy" or "Neutral" though it should be noted that the proportion has now reduced. There are quite a chunk of reviews with "Surprise" emotion and this emotion could be either positive or negative experience. This could explain the drop in proportion of positive reviews.

The negative reviews are further split into reviews labelled as "Sadness", "Disgust", "Fear" and "Anger". This is where the MBS management could come and review such comments to find out the area of improvement. The main reason of such negative sentiment could be determined using technique such as creating a wordcloud of the unigram, bigram and trigram. 