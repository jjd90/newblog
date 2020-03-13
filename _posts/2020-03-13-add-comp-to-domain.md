---
layout: post
title: "Adding a Windows 10 Computer to a Domain"
date: 2020-03-13
categories: Blog
background: '/img/posts/04.jpg'
---

Hi Everyone,

Last week we setup a fresh install of windows 10 on a computer. This week we will be adding that computer 
to the domain that we created a few blog posts back. The reason why we would want to add this computer to 
the domain is:

-	It would make it easier to manage the computer
-	It would make it easier to manage the computers users 
-	It would allow us to perform other actions from a central location 
-	And other cool stuff…

To get started fire up the computer and make sure it is attached to the same network as your domain controller 
(server) and that both are on.

1. The very first thing we need to do is add the computer to the domain. At the log in screen go ahead and 
   sign in.

   ![Instruction1screenshot](/newblog/img/resources/2020-03-13-Post/1.jpg)

2. Next open a file explorer window (manila folder icon). From here we will navigate to the “System” window.

   ![Instruction2screenshot](/newblog/img/resources/2020-03-13-Post/2.jpg)

3. To the left of the explorer window go ahead and right click on “This PC” and select properties. 

   ![Instruction3screenshot](/newblog/img/resources/2020-03-13-Post/3.jpg)

4. At the “System” window go down to “Computer name, domain, and workgroup settings” and select the option to 
   the right named “Change settings”.
   
   ![Instruction4screenshot](/newblog/img/resources/2020-03-13-Post/4.jpg)

5. The “System Properties” window will now show. Click on the option named “Network ID…” to begin launch the 
   “Join a domain or workgroup” window to begin adding the computer to the domain.
   
   ![Instruction5screenshot](/newblog/img/resources/2020-03-13-Post/5.jpg)

6. On the first section named “Select the options that describe your network” leave the default option and 
   then click on “Next”.
   
   ![Instruction6screenshot](/newblog/img/resources/2020-03-13-Post/6.jpg)

7. Next on the “Is your company network on a domain?” leave the default of selection and click on “Next”.

   ![Instruction7screenshot](/newblog/img/resources/2020-03-13-Post/7.jpg)

8. On the next screen read the details of what you will need (password, admin domain username) and then click 
   on “Next”.

9. You will now need to input your domain admin account information and the name of the domain. When done click 
   on “Next”.
   
   ![Instruction9screenshot](/newblog/img/resources/2020-03-13-Post/9.jpg)

10. On the next window you will need to type in the domain again. Make sure to leave the computer name alone, 
    DO NOT changed it. Then click on “Next”.

    ![Instruction10screenshot](/newblog/img/resources/2020-03-13-Post/10.jpg)

11. A window will pop up and you will once again need to provide your credentials and your domain name. Then 
    click on “OK”.
    
    ![Instruction11screenshot](/newblog/img/resources/2020-03-13-Post/11.jpg)

12. The computer will now go through the process of getting added to the domain. If you are successful in 
    adding it, you will see a screen titled “Do you want to enable a domain user account on this computer?”. 
    Select the second option of “Do not add a domain user account” and then click on “Next”.
    
    ![Instruction12screenshot](/newblog/img/resources/2020-03-13-Post/12.jpg)

13. You will now see a window letting you know that you need to restart your computer for the settings to take 
    effect. Go a head and click on “Finish” to get taken back to the “Systems Properties” window.

14. At the “Systems Properties” window go ahead and click on “Okay”. A small window will appear letting you know 
    once again that you need to restart the computer. Click on “Restart Now”.

    ![Instruction14screenshot](/newblog/img/resources/2020-03-13-Post/14.jpg)

15. The computer will go through the restart process.

16. Once you are back at the log in screen you will need to select “Other User” to log into your domain user account. 
    Type your credential and log in.
    
        Note: notice how underneath the password section you now see an 
        indicator that you will be signing into ACME. In other words, 
        you’re signing onto the ACME domain.
        
    ![Instruction16screenshot](/newblog/img/resources/2020-03-13-Post/16.jpg)

Congratulations you have now successfully added a computer to the domain and signed in using a domain user account. 
On the next blog we will be going over some of the ways that the domain controller has affected this computer. 
If you recall we turned on some services such as DHCP, DNS, and Group Policies all of which influence the computer/users 
that are members of the domain. 
