---
date: 2023-01-15

layout: post
title: Launch of new github page
description: Launching al-folio template as my github page
tags: [github page]
categories: app

comments: true
published: true

---

For over 2 years, I have been using the [Beautiful Jekyll by Dean Attali](https://github.com/daattali/beautiful-jekyll) as my github page. No doubt that it was simple and pleasant looking as a github page. However, I have always wanted to use my github page more than just a platform to post. I wanted to use it to promote myself as well as to build up my data science capability and portfolio.

I did a quick google search and found this fantastic github page template - [al-folio](https://github.com/alshedivat/al-folio). It is "_a simple, clean, and responsive Jekyll theme for academics_". It is indeed those! I have to admit that I am not as proficient as I thought I was with git and github but hey, today I learned. 

In my first few attempts, I had trouble running it despite following the instructions. I am not sure what was the mistakes or could it be that the instructions were slightly outdated? I wouldn't say that it was one or the other but I managed to deploy the page after a few trials. 

Anyway, the point of this post is simply to write down what I did in order to deploy it successfully. This will help me to recap what happened previously if ever I need to repeat the whole process again because of some errors.

To begin creating my own github page using al-folio tempalte, I first created a new repository by using this template on github. Thereafter, I gave it a temporary name e.g.`test` or simply name it as `username.github.io` as the repository name. Once that was done, I cloned the repo down to my local machine and went to the `_config.yml` file. In that file, I changed the URL to `username.github.io` and left `baseurl` empty as per the instructions.

I then went back to repo on github then navigated to `Settings` > `Action` > `General`. I had to make sure that "_Allow all actions and reusable workflows_" was selected under the "_Actions permissions_". In my previous attempts, I selected the "_Allow `username`, and select non-`username`, actions and reusable workflow_" (last option). This could be the reason why my page didn't get deployed succesfully in my earlier attempts. 

After that, I went to `Settings` > `Pages` and checked that the source is "_Deploy from a branch_" and the branch is "_gh-pages_". All these changes need to be saved. Once the settings is done, I then pushed my changes to trigger the automatic workflow. The entire workflow typically took a few minutes to complete.

To check the status of the deployment, I went to the `Actions` tab and checked that the "_pages build and deployment_" action was completed and had a green tick on the left side. Or I could simply type in `username.github.io` into the internet browser and check for the changes I made. 

Each push command would have 3 runs - "_Docker Image CI_", "_deploy_" and "_pages-build-deployment_". Once all three runs are successful then the github page would be successfully updated. 

That is how I successfully created this whole github page. It is a rather simple process! It definitely took me a few hours over a day to figure out but hey, I learned something new. I am now 1 step closer to being proficient with git (wherever that place may be).

Cheers.