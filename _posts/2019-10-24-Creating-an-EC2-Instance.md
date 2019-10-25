---
layout: post
title: "Creating an AWS EC2 Instance"
date: 2019-10-24
categories: Blog
background: '/img/posts/04.jpg'
---

Hi Everyone,

For this blog post I will be walking you through the process of creating an EC2 instance in Amazon Web Services using an ubuntu instance and we will set it up so that we can SSH into the instance through a Command Line Interface terminal. Let’s get started:

1.	In AWS navigate to the Services > Compute > EC2 and under the “Create Instance” section select Launch Instance

2.	In the Choose and Amazon Machine Image (AMI) search bar type in “Ubuntu” and select the first result named “Ubuntu Server 18.04 LTS (HVM), SSD Volume Type” then click Select.

3.	Next in the Choose an Instance Type windows leave the default option which should be “General Purpose  t2.micro” this option is apart of the free tier and we will not have to spend any money to use it. At the bottom right click on next.

4.	In the Configure Instance Details window leave the defaults except for the “Network, Subnet, Auto-assign Public IP”. For the network option make sure to select the desired VPC or leave the default on. For the Subnet option make sure to select the subnet that is public otherwise we will not be able to connect to the instance. Lastly for the Auto-assign Public IP option select enable. Click on next to move to the next window.

5.	In the Add Storage window go ahead and leave the default options and click next. 

6.	In the Add Tags windows we will create a new tag with the kay “Name” and in the “Value” section go ahead an create a name for the instance. 

7.	In the Configure Security Group window leave the default option of “Create a new security group” for the Assign a security group option. At the bottom you will we a section with a firewall rule for SSH. Go ahead and leave it as is since we will be using SSH to remote in we need to have this rule. You can as well add additional rules if you would like. When done click on Review and Launch

8.	In the Review and Launch windows verify your option and settings then you can click on the Launch button.

9.	On the next window you will need to download the new keypair then name it and save it to your local computer. This key is very important as it will be used to remote into the instance later.

10.	Once the instance is launched you should navigate to the instances windows and select your new instance then click connect. A window will pop up with detailed instructions on how to connect to the new instance via SSH. I will not include those steps here since they are detailed, and AWS make it clear on what needs to be done.

Congratulation you have created a new EC2 instance in AWS

