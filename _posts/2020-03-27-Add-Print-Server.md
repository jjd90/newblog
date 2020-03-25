---
layout: post
title: "AD DS Print Server & Printer Install"
date: 2020-03-27
categories: Blog
background: '/img/posts/08.jpeg'
---

Hi Everyone,

This week’s blog was supposed to focus on a review of the Active Directory services we installed and 
how those services change once a computer is added to the domain. 

I forgot one rather important topic which is setting up a print server. Having a print server installed 
makes managing printers very easy and it is all done from one place. Doing so also allows for the deployment 
of printers via group policy so you never have to go computer by computer to install a printer. Instead, I 
will be going over how to set up a print server on a server running Active Directory Domain Services (AD DS).

     Note: Prior to beginning make sure that you have a network 
     printer on your network ready and configured with an IP address.

1. We will begin by installing the print server service. Open the “Server Manger Window” and click on “Manage” 
   at the top right and then “Add Roles and Features”.

   ![Instruction1screenshot](/newblog/img/resources/2020-03-27-Post/1.jpg)

2. The “Add Roles and Feature Wizard” window will appear. Go ahead and click “Next”. 

3. At the next section leave the default of “Role-based or feature-based Installation” and click “Next”. Then 
   again on the thirds section named “Server Installation” leave the default and click “Next”.

4. You should now be at the “Sever Roles” section. Look for the Role named “Print and Document Services” and 
   click on the check box. 
   
   ![Instruction4screenshot](/newblog/img/resources/2020-03-27-Post/4.jpg)

5. Upon clicking the check box, a screen will pop up named “Add features that are required for Print and Document 
   Services?”. Leave the defaults and click on “Add Features”.
  
   ![Instruction5screenshot](/newblog/img/resources/2020-03-27-Post/5.jpg)

6. You will then be taken back to the “Server Roles” sections. Click on “Next” to proceed.

7. At the “Features” click “Next”. We won’t be installing features. Then again on the next sections “Things to Note” 
   click on “Next”.

8. You should now be at the “Role Services” section. Here leaves the default selection of “Print Server” checked 
   off and then click on “Next”.

   ![Instruction8screenshot](/newblog/img/resources/2020-03-27-Post/8.jpg)

9. At the “Confirmation” sections click on “Installed” to begin the installation. It will take a few minutes. 
   Once finished click on “Close” to exit out of the “Add Roles and Features Wizard”.

10. Next, we will add a printer to the print server management console. Begin by opening the windows menu and going 
    to “Windows Administrative Tools” and then selecting “Print Management”.
    
    ![Instruction10screenshot](/newblog/img/resources/2020-03-27-Post/10.jpg)

11. The “Print Management” window will open. You should see a window like the screenshot below.  

    ![Instruction11screenshot](/newblog/img/resources/2020-03-27-Post/11.jpg)

12. To begin the installation of a printer, navigate to the left menu then click on “Print Servers” to expand the 
    sub menu. You should now see the server name, click on the name and another list will appear. You want to click 
    in to the “Printers” entry.
    
    ![Instruction12screenshot](/newblog/img/resources/2020-03-27-Post/12.jpg)

13. Once you’re at the printer’s section you will need to right click into the open area and then select the option 
    for “Add Printer…”.
    
    ![Instruction13screenshot](/newblog/img/resources/2020-03-27-Post/13.jpg)

14. The “Network Printer Installation Wizard” window will pop up. Leave the default of “Add TCP/IP or Web Services 
    Printer by IP address or hostname” then click “Next”.
    
    ![Instruction14screenshot](/newblog/img/resources/2020-03-27-Post/14.jpg)

15. You should now be on the IP address section. Change the “Type of device” to “TCP/IP Device”, then enter the IP 
    address of the printer, and leave the check box for “Auto detect” checked off. When done click on “Next”.
    
    ![Instruction15screenshot](/newblog/img/resources/2020-03-27-Post/15.jpg)

16. The wizard will now search for and detect the printer. 

17. Once the wizard has detected the printer you will see the screen below and be asked to provide the driver software. 
    When ready click “Next” to go to the driver selection window.

        Note: In some cases, the wizard will be able to download 
        the driver if it can find it through windows update.  
        
    ![Instruction17screenshot](/newblog/img/resources/2020-03-27-Post/17.jpg)

18. At the driver selection window, you can do one of two things. Search for the driver based on the brand or you can 
    choose “Have Disk…” and upload the driver software yourself. For this tutorial we will choose a preinstalled driver. 
    
        Note: Not all printer brands and drivers will be available. 
        
    ![Instruction18screenshot](/newblog/img/resources/2020-03-27-Post/18.jpg)

19. On the next section, you will be asked to provide details for the printer such as; Printer Name, Share Name, Location, 
    and Comment. The more important field are the Printer and Share names as there are the names that will show when the
    printer is added to a computer. When done filling out click on “Next”.
    
    ![Instruction19screenshot](/newblog/img/resources/2020-03-27-Post/19.jpg)

20. You will now see the details for the printer install. Go ahead and click “Next”.

21. The printer will install and when finished you will see the screen below. Click “Finish” to close the window.

    ![Instruction21screenshot](/newblog/img/resources/2020-03-27-Post/21.jpg)

22. Now back at the printer window you should now see an entry for the printer you created. Like in the image below.

    ![Instruction23screenshot](/newblog/img/resources/2020-03-27-Post/23.jpg)

Congratulation! you have successfully installed a printer on the print server for your domain. Next week I will finally 
cover and review changes that have occurred on our domain controller and domain workstation so you can get a sense of what 
goes on when you have an AD DS environment. 
