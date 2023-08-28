---
layout: post
title: Working with Docker container
description: How to build and use a Docker container for development and deployment?
date: 2023-08-31
tags: [Docker, development, deployment]

comments: true
published: false
---

There are plenty of articles online that could explain what is Docker and how it could benefit your work in developing and deploying your applications and I have been reading them but I just haven't had the hands-on experience of working with Docker. Eventhough the Docker commands seem rather simple like `docker pull`, `docker logs` etc. but how does one actually build a customized Docker image and use it for their own development work? 

I have been creating virtual environments to test and develop my apps. However, it is tedious to constantly create a virtual environment each time as I work on multiple projects across multiple laptops. Not to mention, the virtual environment would take up memory space in my laptops. Thus, I have decided to learn how to use Docker.

That, and also, because I would want to deploy some dashboards that I have in mind using a Docker image on AWS. Anyway, you can find the instructions in the sections below on how to build a Docker image, developing and testing scripts in a Docker container as well as conducting EDA using Jupyter notebooks in the Docker container.


# Basic instructions
This section teaches you how to build a basic Docker image and container using a `Dockerfile`. 

1. Create a `Dockerfile` (without extension). 
* An example `Dockerfile` that I am currently using is as below. 
* Though you are welcomed to further customize it after reading this [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) by Docker.
~~~
# Use an official Python runtime as the base image
FROM python:3.8-slim

# Set the working directory inside the container
WORKDIR /home

# COPY requirements file
COPY requirements.txt .

# Install required Python packages using pip
RUN pip install --upgrade pip
RUN pip install -r requirements.txt 

# INSERT COMMAND HERE
~~~

2. Build a Docker image by running the command below in the terminal.
~~~
docker build -t <IMAGE_NAME> . 
~~~
* Make sure to give your image a unique name so that you could easily identify it.
* Don't forget the `.` at the end!

3. Run a Docker container using your Docker image by running the command below in the terminal.
~~~
docker run -it -v /path/to/local/directory:/home  -p 9999:9999 --name <CONTAINER_NAME> <IMAGE_NAME>
~~~
* The `-v /path/to/local/directory:/home` argument is to mount your local volume to your container for subsequent development.
* Mounting your volume is necessary if you wish to develop and save your codes in your local volume. Else, all is lost when the container is terminated.
* Feel free to give your own unique `<CONTAINER_NAME>` such as `homey`, `hawker`.
* `-p 9999:9999` only necessary if your Python script runs a web service or requires network access.


# Developing with a mounted local volume
This section teaches you how to develop your codes in a container while ensuring that your codes are saved to your local directory instead of the container directory. 

1. Build and run a Docker container using the instructions in [Basic instructions](#basic-instructions) with the below command in the `Dockerfile`.
~~~
# Command to keep the container running (python script)
CMD tail -f /dev/null
~~~
* The `CMD tail -f /dev/null` line in the Dockerfile is used to keep the container running, so you can attach to it with VSCode.

2. Attach the running container to VSCode (which I am currently using. If you're using PyCharm or Spyder etc., I'm so sorry I couldn't help you :( )
* Install the "Remote - Containers" extension in VSCode if you haven't already.
* In the bottom-left corner, click on the blue icon ("Open a Remote Window").
* Select "Remote-Containers: Attach to Running Container..." from the menu.
* Select the container you launched in the previous step.
* A new VSCode instance will be launched.

3. In the new VSCode instance, navigate to your working directory in the container. 
* In this example, my working directory is `home`.
* It is not necessary to install any extensions in this container VSCode instance.

4. Create, edit and/or delete your `.py` files away. These files will appear in your chosen local directory as well. Feel free to test out the steps. 

5. To run the script, simply open a bash terminal and run the following command: 
~~~
python <PY_NAME>.py
~~~

6. To exit the container, simply close the VSCode instance and stop/delete the container in Docker.
* You could restart the container and reattach to the VSCode before continue development. There is no need to remount the local volume. This is provided that you did not delete the instance.
* Once the container is deleted, you will have to mount your local volume again.

# EDA with Jupyter notebook
1. Build and run a Docker container using the instructions in [Basic instructions](#basic-instructions) with the additional run and command lines in the `Dockerfile`.
* Ensure to install `jupyter`. Else, you wouldn't be able to use Jupyter notebook in the container.
~~~
RUN pip install jupyter

# Command to run and open jupyter notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
~~~

2. In the terminal, open the provided `http://127.0.0.1:<PORT_NO>/tree?token=<TOKEN>` in the browser to access your local Jupyter server.

3. In your local Jupyter server, you may create, edit and delete your notebooks. 

4. To exit the container, simply close the VSCode instance and stop/delete the container in Docker.
* You could restart the container in Docker and access the Jupyter server via the provided link in Docker container logs. There is no need to reattach your local volume. This is provided that you did not delete the container.
* Once the container is deleted, you will have to mount your local volume again.

# The end
I hope you, and I!, have learned something new today. This article is short, simple, and most definitely not exhaustive. I am sure there are more ways, and also better ways, to achieve what I have done. But I really hope that this is the start of your Docker journey. 

Cheers. 