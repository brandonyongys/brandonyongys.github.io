---
layout: post
title: Analysis of Reddit Singapore Daily Thread - Part 3
tags: [reddit]
comments: true
published: false
---

This will be my first attempt to do a proper text analysis. In this part, I am going to determine the most frequent bigram and trigram, that is the most frequently used two-word and three-word terms. The bigram and trigram are then plotted into a word cloud, as shown in the previous section. This section is particularly difficult because there are a number of things that I have to do first before I can finally determine the most frequent bigram and trigram.

First, there are modern slangs that I have to replace with such as "gonna" to "going to" and "wanna" to "want to". These slangs have to be replaced first or else these words would be lemmatized into two separate words, which will affect the word cloud. Second, there are a number of url that need to be removed. 

The challenging part of the preprocessing step is removing the emoji. I have searched online and used a lot of the suggested emoji removal step and it's not 100% successful. Despite that, I still manage to remove most of it and left a few emoji that may skew the results in the end a little bit. But I'll take that as a success for a first attempt.

### 
