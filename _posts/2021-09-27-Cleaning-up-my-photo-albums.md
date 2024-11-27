---
layout: post
title: Cleaning up my photo albums
tags: [photos, images]
comments: true
published: false

date:   2021-09-27
categories: image analysis
---

I have been taking pictures with my phone especially when I travel overseas for a holiday or meeting up with friends whom I have not met for a period of time. Taking these pictures are meant to capture the moments so that I would be able to look back at these photos when I am older. Once in a while, I would just transfer the photos over to my harddrive and promise myself that I would review it soon.

Again and again, I promise myself that and what do you know. I have procrastinated on it for a few years now. There are just too many photos for me to review now, although I would enjoy reliving the memories again. 

And when I take photos, I would snap a picture of the same scene a few times and that would mean I would have to review the duplicated photos as well. That bunch of duplicated photos is gonna take me longer than expected.

I then went on and search for a way to automatically identify and remove the duplicated photos using programming. Lo and behold, there is such method (nothing surprising actually). I am mainly applying what I had learned [here](https://www.pyimagesearch.com/2020/04/20/detect-and-remove-duplicate-images-from-a-dataset-for-deep-learning/) since it is rather straight forward and simple. 


The image detection is mainly dependent on the hashing algorithm (for more details, see [here](https://www.pyimagesearch.com/2017/11/27/image-hashing-opencv-python/)). In general, how the hashing algorithm works is:

1. Convert the image to a grayscale _(optional)_
1. Resize the image to a n+1 x n, where n is typically 8.
1. Calculate the difference between 2 adjacent columns.
1. Calculate the hash value.

Note that the first step is optional. Converting to a grayscale image would speed up the computation time and eliminate the error where 2 perceptually similar images are identified as different images due to a single pixel change.

The image is resized to n+1 x n is because of the following step. Typically the hash is a 64 bit and to generate a 64 bit, you would need an 8x8 image. Given that we are calculating the difference between 2 adjacent columns to get the 8 columns, we would need an additional column.


Once I understood the general mechanism, I then coded things up using OOP. Although it is a rather simple exercise and I could easily put it in a simple Jupyter notebook, I wanted to code it as OOP because I wanted to practice coding it. 

The main difference between my code and the source code is what to do with the duplicated photos. Rather than deleting it, I saved the alternative photos in a folder called "Duplicated photos" because I wanted to review and make sure I saved the correct photo.

When I run the code, I did not know how many photos were there but I coded it such that it prints the progress of the hashing process. Though that, I realize that I had over 3.5k photos to review and it was done within 2 minutes. If I were to review it manually, it would have taken me over a week or two. All in all, I saved about almost 2 weeks of effort after spending about 2 days coding it (well, would have been faster but I was procrastinating as well haha..).

I am happy to have learn something new especially image processing. All the stuffs I've done at work are mainly with tabular data. So there isn't a need to learn packages like cv2. 

Next step is to learn how to process videos. I have also taken videos and generally the content is the same but with varying duration. Am I gonna watch the entire video and decide which to delete? I hope not.

