---
layout: post
title: "Project 0 Continued"
date: 2019-10-11
categories: Blog
background: '/img/bg-post.jpg'
---


Hi Everyone,

This week marks the continuation of work on our Project 0. This post will be relatively small due to the continued work. For the most part we are in full swing and tasked are being worked on as well as documented through GitHub. I am about 80% done with the Ansible playbook. 
To my surprise the play book code is going to be relatively short as compared to the LAMP stack lab. This is due to less requirements, the professor confirmed this past Saturday that we only really needed apache and PHP installed on out server to host our website. 
For the most part my playbook is outlined as follows:
-	Install Apache2 
-	Start Apache2
-	Install PHP
-	Copy over the new apache configuration file
-	Copy over the index html
-	Restart Apache2 
We have encountered issues with other portions of the project though. For some reason we cannot ssh into our EC2 instance anymore and the VPC process has had its hiccups as well. We are unsure if the issues are related to public/private key encryption or if its related to the VPC issues that we are having. I will have a brief update on next weeks post with the outcome. 
If we can manage to fix these issues by Friday October 11th we will be toast and I say that because my portion is dependent on connecting to the instance and running the playbook to get the website up and running.
We meet again on October 9th and once again had no luck getting the instance up. WE ARE OFFICIALLY IN PANIC MODE!!

