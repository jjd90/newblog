---
layout: post
title: "AD DS Deploy Software Installs Using Group Policy"
date: 2020-04-17
categories: Blog
background: '/img/bg-post.jpg'
---

Hi Everyone, 

Welcome back to another weekly edition of my CIT blog. For this week we will be sticking with group policies. 
Last week we created a network folder and deployed it via group policy. This week we will be deploying a software 
installation. Deploying software via a group policy if very beneficial, it saves time and can be deployed in 
minutes. We will be deploying Google chrome for this tutorial. 

There are two types of methods to deploy the software, Assign and Publish. When assigning the software, it will
automatically be installed on every single computer and for all users. If you choose to publish the software, 
then the user will need to install it via add or remove programs. I will point out where you set this option in 
the steps below.

1. To get started we need to specify the folder in which the software will be installed. You can either create a 
   new network shared folder or use an existing one. Navigate to the folder and copy the software package into it.

2. Next, open the group policy management window.

3. At the group policy window go ahead and either select and existing group policy or create a new one. For this 
   purpose, I will use the existing group policy. Right click on the policy and select “Edit…”.

4. The Group Policy Management Editor will pop up. Here we will be setting up the specific policy settings to 
   deploy the software.

5. Navigate to the following sections, Computer Configuration > Policies > Software Settings then right click and 
   select “New” then “Package…” 

6. A windows explorer windows will open. Go ahead and navigate to the location on the network shared folder where 
   you placed the software that you want to install.

7. After selecting the software, you will get a pop up. This is where you will select the type of installation that 
   you want. Details are below. I will go with the assign option; you can choose the option that best suites your 
   needs. Then click on “Okay”.

Published: User must install software via add or remove programs.
Assigned: Automatically install on computer for all users.

8. You should now see an entry for the software deployment. 

9. That’s it for group policy portion. You will now need to test the policy by heading over to a workstation. A 
   restart of the computer should be enough to receive the policy update. If that doesn’t work, try running the 
   following command in CMD “gpupdate /force” and then restart the workstation.

10. If all goes well when you sign in the policy will begin to install the software. You can check this by navigating 
    to the Task Manger on the workstation and identifying the “Microsoft Installer” process. 

11. Once finished you will see a chrome shortcut appear on the desktop.

Congratulations you have successfully deployed a software installation using a group policy. If you experience any 
issues check your deployment settings again. You can also reach out to me for help. 
