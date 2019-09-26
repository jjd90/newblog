---
layout: post
title: "Working with Ansible"
date: 2019-09-20
categories: Blog
background: '/PATH_TO_IMAGE'
---

Hi Everyone,

Welcome back for another weekly edition of CIT 480 Blog.
	
This week I was tasked with creating two Ansible playbook files. The first playbook was required to install traceroute, create two new groups, create users for each group, and lastly set permission for both groups. The second playbook was required to install a LAMP environment, the affinity, and composer. Being that I had never heard of Ansible I knew I was in for a good learning experience.
	
Like with all projects I began with a simple google search. Next thing you know I have about fifteen tabs open on my web browser with no idea, in hell, on what to exactly do. After a few minutes of back and forth between webpage tutorials and youtube videos I started to understand what exactly an Ansible playbook is all about. It is a simple, yet complex, file written in YML that can be used to configure multiple systems with a simple command and a press of the enter key. 

Now that I was aware about what exactly an Ansible playbook the next question was, “What’s the structure and the syntax?”. Once again, I found myself overloading on the numerous amounts of tutorials and videos that were available online. Eventually stumbling on a webpage where I began to understand the process and structure. Ansible files are easy to structure once you start to understand how commands are written out (sample command below). 
 	
At the top of the file you start by specifying the target hosts and then right underneath you start to list the task you want to complete. Ansible playbooks use what are called modules to specify the commands that the playbooks should run. You would normally run an apache install by typing out, “apt-get install apache2”. In Ansible the apt-get command, and any other command you can think of, has a corresponding module. For apt-get that module is apt.
	
For most modules the module (command) type is superseded by a name field which is more of a comment that explains what that portion of the task with do as seen above I gave the task a name of “Install Apache2”. Second you specify the module (command) that you want to call in my case the “apt” module is the ansible equivalent of “apt-get”. Below that the name of the software package to be installed should be specified, in my example I specified “apache2”. Then the state is set to latest for the latest version. 

For the apt module you have to specify that you want to run a apt-get so you set the force_apt_get to yes. Lastly, I set the cache to be updated. Below is the sample:
	
  - hosts: localhost
  - remote_user: root
  - tasks:
  	- name: install apache2
	- apt:
	     - name: apache2
	     - state: latest
	     - force_apt_get: yes
	     - update_cache: yes
             
Ultimately, having to work on an Ansible playbook was not a daunting as I originally thought it would be. Yes, there is a new syntax that need to be learned but that’s nothing when you think about the knowledge that is gained in the process. 

Thanks for reading!

P.S. Since submitting this blog I have yet to finish the playbooks. I will give an update on next weeks blog. Stay tuned!

