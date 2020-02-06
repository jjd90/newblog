---
layout: post
title: "Windows Server AD DS Install and Domain Controller Promotion"
date: 2020-02-07
categories: Blog
background: '/img/posts/04.jpeg'
---

Hi Everyone,

	This week we will be moving on in our series involving Windows systems and implementing
  Active Directory Domain Services (AD DS) and other services. This blog post will focus
  on actually installing AD DS and promoting our server into a Domain Controller. If you
  have yet to prepare a server for AD DS to be installed, please refer to my previous post
  otherwise if you have already prepared your server continue below.

1. Let’s start off by powering on the server and letting it load up so that the Windows Server
   Manager window gets displayed.

      Note: The windows server page is were all roles and feature are installed from.
      This window as well gives you information on the server.

2. To install the AD DS role, start by clicking “Manage” at the top right and then selecting “Add
   Roles and Feature”. The “Add Roles Features Wizard” will now be displayed.

3. The add roles features wizard will show the “Before you begin” section, go ahead and click on
   “Next”.

4. On the “Installation Type” sections go ahead and leave the default selected “Role-based or
   feature-based installation” and then click on “Next”.

5. On the next section “Server Selection” leave the defaults and then click on “Next”.

6. At last we get to the “Server Roles” section. Here we would choose all the server roles we would
   want to install. For our purposes click the box next to “Active Directory Domain Services”.

      Note: The “File and Storage services” box will also be checked off. This is a
      default role that will already be installed. It will be used by AD DS services
      and gives you the ability to set up network shared folders.

7. Instantly a window will pop up asking, “Add features that are required for Active Directory Domain
   Services?” leave the defaults and click “add features”. Then back at the server roles section click
   on “Next”.

8. On the next section called “Features” leave the defaults and click on “Next”.

9. You will now be at the “AD DS” section which gives you information on Active Directory. When done
   reading click on “Next”.

      Note: The wording lets you know that the DNS role is required and will be
      automatically installed. That is the reason we didn’t not choose it back
      at the Roles section.

10. Finally, you will get to the “Confirmation” section. You will see an overview of what will be installed
    as well as a checkbox at the top to allow the serve to automatically restart once the install in finish.
    Click the check box, on the pop-up click “yes” and then back at the “Confirmation” section click on
    “Install”.

11.	The installation of AD DS will take a few minutes. Once finished you can click on the “close” button. The
    server will not need a restart, but I recommend that you restart the server either way.

12.	After the server restarts and the server manager window load you will notice that there is a caution sign
    at the top right on the top right of the window next to manage. Click on the flag.

13.	A small window will pop up saying that the server will need to be promoted to a domain controller. Go ahead
    and click on the blue wording.

14.	 The “Active Directory Domain Services Configuration Wizard” window will pop up and the “Deployment
     Configuration” section will be displayed. Select the option for “Add New Forest” and then type in the
     name that you will give your domain. I will be using acme.local then click “next”.

15.	Next, on the “Domain Controller Options” leave the default functional levels and controller capabilities.
    Then create a password for the Directory Services Restore Mode (DSRM) and then click “Next”.

      Note: make sure to save the password. If you ever have to recover the domain
      you will need it.

16.	For the next three sections “DNS Options”, “Additional Options”, and “Paths” leave the defaults and click
    on “Next”.

17.	At the “Review Options” window glance over the settings you specified to make sure everything looks good.
    Once ready click on “Next”.

18.	The wizard will not run a prerequisite check to make sure that the promotion to a domain controller doesn’t
    have any issues. You will more that likely see some caution alerts but don’t worry we should still be able
    to continue with the promotion. Go ahead and click on “Install”.

    Note: Ignore the DNS delegation message. This error occurs because we don’t
    have a current DNS server on the network. This server will eventually become
    that DNS server.

19.	The promotion process will take a few minutes. Once completed the server will restart.

Congratulation you have successfully installed the AD DS role and promoted the server to a domain controller.
On the next blog post we will configure some for settings for the domain controller.
