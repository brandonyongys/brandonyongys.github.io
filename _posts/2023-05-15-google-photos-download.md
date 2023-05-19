---
date: 2023-05-15

layout: post
title: Automating Google Photos download # Project post title
description: What's the lazy way?

comments: true
published: true

---
# The Problem
<hr>

For the past five years, I have been a big admirer of Google and have used several of their services including Google Photos, Gmail, and Google Maps. I particularly rely on Google Photos to automatically upload and store my photos and videos. While Google offers free 15 GB of storage, recently, I have been capturing a lot of videos during special occasions, and they are quite long, resulting in me exceeding the free storage limit. To ensure I can continue backing up my photos and videos, I had to upgrade to the basic membership, which offers 100GB of storage, at a reasonable monthly fee of $2.79. 

The amount may not seem like much at the moment. However, the amount of media stored in my Google Photos will only keep going up and I would have to constantly delete unwanted photos. Considering the potential cost over my lifetime and possible price increases by Google, I have adapted a script that utilizes Google Photos REST API to download all files automatically. This way, I can save money and also have offline backups of my precious memories in the event that I lost access to my Google account.

# The Solution
<hr>

To create this script, I first sought out resources online to better understand and experiment with the Google Photos REST API. I found a helpful [Medium post](https://towardsdatascience.com/how-to-download-images-from-google-photos-using-python-and-photos-library-api-6f9c1e60a3f3) by Dominik Polzer (Jupyter notebook may be found [here](https://github.com/polzerdo55862/google-photos-api/blob/main/Google_API.ipynb)), which provided me with the necessary knowledge to use the API. After studying the code and playing around with it, I was able to successfully adapt it for my own use. 

The codes written by Dominik work well generally and it is able to connect to your Google Photos with no issue after following the provided steps to obtain your credentials. However, upon further testing, I found that there are generally two main issues:

1. All images are downloaded as 512 by 288  instead of the original dimension.
2. All videos are downloaded as jpg instead of mp4 files.

With that said, Dominik's notebook would be sufficient if you intend to download all media as images in 512 by 288 dimension. My adapted codes may be found on my [github](https://github.com/brandonyongys/gphotos).

# The Code
<hr>

## The credentials

The `GooglePhotosApi`, as found in my `gphotos.py` file, is as written by Dominik. The only change I made is to add a new function, `delete_pickle_file`, to delete the token file after each run. This is to, in my opinion, add a layer of security so that the user does not accidentally upload the token file online, which allows others to access the user's Google Photos. Though the user could always setup a `gitignore` file

## The downloads

The download functions are found in the `gphotos_download.py` file and they have been adapted from Dominik's original codes to address the two issues I've highlighted earlier. To resolve the issues, I've referenced the [Google Photos API](https://developers.google.com/photos/library/guides/access-media-items) on accessing media items. 

The photo and video media files would generally have the same set of reponse. The only difference is in the `mediaMetadata`. The width, height and creation time would be available for both photo and video. However, both photo and video would have slightly different metadata of the camera, as shown below (as quoted from Google Photos API web):

**Metadata for photo:**
~~~
"mediaMetadata": {
"width": "media-item-width",
"height": "media-item-height",
"creationTime": "media-item-creation-time",
"photo": {
    "cameraMake": "make-of-the-camera",
    "cameraModel": "model-of-the-camera",
    "focalLength": "focal-length-of-the-camera-lens",
    "apertureFNumber": "aperture-f-number-of-the-camera-lens",
    "isoEquivalent": "iso-of-the-camera",
    "exposureTime": "exposure-time-of-the-camera-aperture"
    }
  }
~~~

**Metadata for video:**
~~~
"mediaMetadata": {
"width": "media-item-width",
"height": "media-item-height",
"creationTime": "media-item-creation-time",
"video": {
    "cameraMake": "make-of-the-camera",
    "cameraModel": "model-of-the-camera",
    "fps": "frame-rate-of-the-video",
    "status": "READY"
    },
  }
~~~

* **Issue 1:** All images are downloaded as xxx by xxx instead of the original dimension.
    * In order to download the photos as per the original dimension, the width and height would need to be extracted.
    * These information are then appended to the end of the `baseURL` with the line: `url += f"=w{item['width']}-h{item['height']}"` where `item` is the media item, `width` and `height` are the original dimension.

* **Issue 2:** All videos are downloaded as jpg instead of mp4 files
    * In order to download the videos as mp4 files, it would need to be identified correctly first. Hence, the check for `video` in the `mediaMetadata`.
    * The `baseURL` is then appended with `=dv` with the line: `url += f"=dv"`

I've also adapted the codes to allow the user to either download photos and/or videos. This is especially useful in my use case where videos are taking up 15GB (my entire free storage) and I could simply download them without having to screen through my Google Photos manually.

Though I would have to acknowledge that there are some limitations to the codes. The first is that there is a lack of ability of delete the media on Google Photos after successful download. According to this [issue tracker](https://issuetracker.google.com/issues/80162783?pli=1), this API call would not be available as of Feb 2022. 


# The End
<hr>

While my code may not be the most polished or organized, I am pleased with its functionality and the benefits it provides for me and others who are seeking to save on their storage usage. I would like to say thank you and give the credit to Dominik Polzer, who has very kindly posted a helpful Medium post.

