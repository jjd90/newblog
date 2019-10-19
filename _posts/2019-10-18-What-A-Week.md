---
layout: post
title: "What a Week"
date: 2019-10-18
categories: Blog
background: '/img/bg-post.jpg'
---

Hi Everyone,


What a week this has been, due to a massive wildfire that affected Porter Ranch mountains and the surrounding cities. CSUN closed the campus down for the weekend which meant that our project presentation had to be pushed another week. While I should be cheering with joy, I was not that happy about it. 

Backtracking to where I left off in last weeks post. Our group had a major issue on our hands, none of us could access our EC2 instance. We were officially in panic mode, I was lucky enough to have my Thursday class cancelled and that mean having the time to work on the VPC. I knew that If I couldn’t get it fixed by the end of the day we would be screwed.  

I went to work and after trial and error I was able to find the issue that was causing our issue with the VPC and accessing the EC2 instance. First off, our VPC routing table was all jacked up. Well at least the public IP subnet routing portion. We were missing the routing table entry that forwards traffic to the outside or the world wide web. In AWS the entry is IP/subnet  0.0.0.0/0 once I added the route, I went back to test our EC2 instance but I was still having issues. 

The next step was to verify what subnet the EC2 instance was on. After looking into it I found that our EC2 instance was on a private subnet within our VPC. Being that the private subnets do not route to the outside it explained why we couldn’t SSH into our instance. Unfortunately, you can’t just switch the subnet of an EC2 instance so what I had to do was create an image from the existing instance then create a new EC2 instance. At last, I was successful in accessing the EC2 instance. It was a relief.

My work wasn’t done though, next came the actual creation of the webserver and all the fun that comes with launching a HTTPS site using Apache2 and a custom Domain. For the most part it wasn’t as difficult as I thought it would be. My major issue was getting certificates created for our site. Luckily, one of our classmates shared the CertBot utility which saved my butt and finally got our website to show up via HTTPS. 

The real kicker is that about 10 minutes after I finished all this work on Friday (10/11/19). I got an email from CSUN that classes had been cancelled for the weekend. You had to be kidding me all that work and we wouldn’t get to present. I was upset but on the bright side, we get more time to prepare for our presentation. 


Hopefully it goes well, I’ll make sure to let you know how it went on next weeks post. 

