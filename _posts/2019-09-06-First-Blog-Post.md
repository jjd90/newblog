---
layout: post
title:  "CIT 480 The Beginning"
date:   2019-09-06 
categories: Blog
background: '/PATH_TO_IMAGE' 
---

Welcome to my first blog post!

My name is Juan, but I prefer to go by Johnny. I’m currently a senior majoring in Computer Information Technology and minoring in Anthropology. Yes!, it’s a weird combination CIT and Anthropology but I have to admit that while taking an archeology I grew to like it a lot. Anyways, back to the important topic this CIT 480 blog. The goal is to update my page with a weekly blog post from now until the end of the semester. Wish me Luck!

To kick off my first blog post, I will be writing about my experience with trying to complete the first lab and creating my first ever github blog page. Initially the lab seemed like it would be a piece of cake that was until page 9 when a dreaded error message began. After creating and logging into a docker container named cit160; and using the guest account to run the “class_setup” command the process would instantly fail.

Since I couldn’t successfully get the command to run correctly. I moved on to the next step in which I connected over SSH to the CSUN server.  Knowing that I wouldn’t be able to complete the epilogue steps within the cit160 container I had created. I opted to run the same commands on the CSUN SSH server which worked like a charm. I ended up copying the lab report file from the CSUN SSH server over to my desktop and that was that for the lab. Mission Accomplished!

The Blog portion was much more fun to complete than the Lab. Once you do the research and learn the basics of how git hub commands work it is a smooth process. You install Jekyll on your machine, create the folder and files that will hold all the necessary information for your blog page, then push all those files and folders to a github repository.

Lastly. You create a secondary branch called “gh-pages” which github recognizes. Github instantly host the contents of the “gh-pages” as a website via a personalized link. Mine happens to be:

https://jjd90.github.io/blog/

In conclusion, I have to admit that learning github and Jekyll was a much more fun process for me while using docker and trying to get the lab completed ended up being much more complex than I figured it would be. As I write this, I have yet to get the class_setup to run successfully on my docker cit160 container.

Thanks for reading!

[UPDATE]
 I was eventually able to figure it out with the help of the professor. It turned out that I had a bad container and all I needed to do was blow it up and recreate it (mind blown). Then again, the professor had mentioned that containers are designed to be easy create or delete when needed.

