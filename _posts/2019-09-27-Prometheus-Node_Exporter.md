---
layout: post
title:  "Prometheus"
date:   2019-09-26
categories: Blog
---


Hi Everyone,

Welcome back for another weekly edition of CIT 480 Blog.
	
I wanted to start off with a recap/update on last week’s Lab 2. After some troubleshooting and research, I was finally able to complete the Ansible playbooks that I was working on. I have to admit that it was a challenging lab to me, but I am grateful with the outcome and especially with the amount of knowledge I gained.

Moving forward, this week’s lab involved working with Prometheus, another piece of software unknown to me. As always, I began with a little bit of research on Prometheus, so that I could understand what exactly I am working on. Prometheus is an open source system monitoring and alerting software tool. The lab involved creating a new docker container and installing Prometheus on it as well as node_explorer. 

The process went smooth for the most from beginning to end. Once the docker container is fired up I installed updates as well as wget and Prometheus. I ended up learning about the tar command which was a good thing. Once I verified that Prometheus was up and running through my browser, I took the required screenshot and I was done.

The second process involved installing node_exporter and using Prometheus to bring up CPU metrics on the local container. Node_exporter is an add on to Prometheus that gives the ability to track node metrics like CPU usage and such. 

I ended up creating a new container for this section and installing Prometheus all over again. Then I installed node_exporter which was as well a smooth install. Once installed and started node_exporter goes to work. I brought up a browser window and connected to Prometheus then I brought up the cpu metric graph took a screenshot. That was it the lab had been completed and I done. 

