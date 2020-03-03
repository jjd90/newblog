---
layout: post
title: "Installing Windows 10 Pro For Domain Environment"
date: 2020-03-06
categories: Blog
background: '/img/posts/04.jpg'
---

Hi Everyone,

Now that we have installed and set up a Domain Controller. We should check that some of the services/roles
that we installed actually work. To do so we will need a workstation that we can setup on the domain and
then use to check the various services/roles. I will be breaking down this process down into two separate
post. The first will deal with installing a fresh install of Windows 10 pro and the second post will deal
with checking that the services / roles that we installed work. With that being said let’s go ahead and
get started. 

        Note: Like I did with the domain controller, I will be using a
        virtual environment.  It is the fastest and easiest way to set
        up an environment for these purposes. If you are going to use a
        physical computer, make sure that it is on the same network as
        your domain controller.

1. Start by booting up the computer to the Windows 10 install image.

        Note: you can use a USB or CD if your computer has one. I will
        be utilizing just he ISO file since this is a virtual environment.

2. You should see the initial window below. Click on “Next” then click on “Install Now”.

   ![Instruction2screenshot](/newblog/img/resources/2020-03-06-Post/2.jpg)

3. At the “Activate Windows” screen enter a license key if you have one otherwise select the option for
   “I don’t have a product key”.
   
   ![Instruction3screenshot](/newblog/img/resources/2020-03-06-Post/3.jpg)

4. Next, of the operating system selection screen choose the option for “Windows 10 Pro” then click on
   “Next”.

        Note: Only the Pro installation comes with the ability to add
        the computer to the domain. DO NOT choose any other option but
        Pro or else you will need to go through this initial process
        again.
        
   ![Instruction4screenshot](/newblog/img/resources/2020-03-06-Post/4.jpg)

5. On the licensing window accept the license terms by checking off the box next to “I accept the license
   terms” and then click on “Next”.
   
   ![Instruction5screenshot](/newblog/img/resources/2020-03-06-Post/5.jpg)

6. On the “Installation Type” window go ahead and select “Custom: Install Windows Only (advanced)”.

   ![Instruction6screenshot](/newblog/img/resources/2020-03-06-Post/6.jpg)

7. Next, Select the drive that you would like to install windows on. I only have one drive available but
   depending on your resources you might have additional drives. Make sure to select the correct one
   (usually starts with “Drive 0”). Then click “Next”.
   
   ![Instruction7screenshot](/newblog/img/resources/2020-03-06-Post/7.jpg)

8. Now windows 10 will begin installing. This process will take a few minutes to complete. The installation
   will restart once finished.
   
   ![Instruction8screenshot](/newblog/img/resources/2020-03-06-Post/8.jpg)

9. Upon restarting the installation will go through a setup process and you will see a window like the
   one below.
   
   ![Instruction9screenshot](/newblog/img/resources/2020-03-06-Post/9.jpg)

10. Once all that setup is completed you will be taken to the user set up screen. The first thing you will
    do is select the region. In our case it is the “United States”. Click on “Yes”.
    
    ![Instruction10screenshot](/newblog/img/resources/2020-03-06-Post/10.jpg)

11. The next two steps will focus on the keyboard layout. On the first step choose “US” as the keyboard
    layout and then click on “Yes”. The following step will ask if you would like to install a secondary
    keyboard layout. Go ahead and click on “Skip”.

12. Now the network will be setup and updated will be installed. Make sure your installation is hooked
    up to a network. 

        Note: In Virtual Box when first installing an OS it will be
        connected to a network which will allow internet access.  I
        will be moving it over to the network I created and added the
        DC too later behind the scenes

13. Now you should be at the “How would you like to set up?” window. Go ahead and select the option for
    “Set up for an organization”. Then click on “Next”.
    
    ![Instruction13screenshot](/newblog/img/resources/2020-03-06-Post/13.jpg)

14. On the following window DO NOT sign in with a Microsoft account. Instead choose the option for
    “Domain Join Instead”.

    ![Instruction14screenshot](/newblog/img/resources/2020-03-06-Post/14.jpg)

15. You will now be at the user setup window. Go ahead and enter the name for the local admin account
    that you will like to use. I will use the following “acmeadm”. Then click on “Next”.
    
    ![Instruction15screenshot](/newblog/img/resources/2020-03-06-Post/15.jpg)

16. Now you will need to create a password for the user. Make sure to make it complex but memorable.
    Then click on “Next” and enter the password again on the confirmation window.

17. Up next is the security window screen. You will need to choose and answer 3 security questions. 

    ![Instruction17screenshot](/newblog/img/resources/2020-03-06-Post/17.jpg)

18. For the next option “activity history” click on “yes”. Then after that for “digital assistant”
    click on “Accept”. Lastly, for the privacy settings leave the default and click on “Accept”.

19. Once all of this is finished you will be taken to the desktop. The last thing we will do is change
    the computer name. Go ahead an open the file explorer and then to the left right click on “This PC”
    and then select “Properties”.

    ![Instruction19screenshot](/newblog/img/resources/2020-03-06-Post/19.jpg)

20. You will now be at the system window. Under the section called “Computer name, domain, and workgroup
    settings” click on the option to the right called “Change Settings”.
    
    ![Instruction20screenshot](/newblog/img/resources/2020-03-06-Post/20.jpg)

21. The “Systems Property” window will pop up and you will need to click on the option to the bottom named
    “Change..”. The description to the left starts with “To rename this computer…”
    
    ![Instruction21screenshot](/newblog/img/resources/2020-03-06-Post/21.jpg)

22. On the window that pops up, “Computer Name/Domain Changes”, go ahead and type a good computer name. I
    will use “acme-user-pc1”. Then go ahead and click “OK”.
    
    ![Instruction22screenshot](/newblog/img/resources/2020-03-06-Post/22.jpg)

23. Lastly you will be prompted to restart the computer, Click “Okay” and then on back at the “System
    Properties” window click on close. A small window will pop up and go ahead and select “Restart Now”.

Congratulations, you have successfully installed a fresh copy on windows 10 and changed the computer name 
in preparation to add it to the domain which we will do on next weeks blog. Thanks for reading!
