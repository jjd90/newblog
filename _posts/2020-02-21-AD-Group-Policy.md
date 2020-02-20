---
layout: post
title: "Active Directory Group Policy Management"
date: 2020-02-21
categories: Blog
background: '/img/posts/04.jpg'
---

Hi Everyone,

Moving forward with the series of blog post focusing on AD DS we will be focusing on creating group policies.
When working in a windows environment you will be asked to create group policies for computers or users.

Think of group policies as permissions that allow you to control what a user or computer can do. From the group
policy management window, you can control every single user, group, or computer that is apart of your domain.
For our purposes we will be creating a simple Group Policy Object (GPO) to control user settings. We will not
dive into the computer portion on this post because we have yet to add computers to our domain. I’m leaving that
process for another blog later.

If you need the actual definitions here it is:
         
          Group Policy Management is a feature that controls the working environment 
          of user accounts and computer accounts and provides centralized management 
          and configuration of operating systems, applications, and users' settings 
          in an Active Directory environment.

1. Start by opening the “Group Policy Management” snap-in located under “Administrative Tools”.

   ![Instruction1screenshot](/newblog/img/resources/2020-02-21-Post/1.jpg)

2. On the left-hand side, you should see the user and computer folders that we created on the last blog post dealing
   with users and computers.
   
   ![Instruction2screenshot](/newblog/img/resources/2020-02-21-Post/2.jpg)
   
3. Go ahead and expand the folder labeled “Group Policy Objects” to discover the current two policies that are active.
   One is called “Default Domain Controller” and the other “Default Domain Policy”.
   
   ![Instruction3screenshot](/newblog/img/resources/2020-02-21-Post/3.jpg)

4. To keep it simple for us we will be editing the “Default Domain Policy”. In a professional environment I recommend 
   creating a copy of the “Default Domain Policy” and using that copy as the primary policy. 

5. Go ahead and right click on the “Default Domain Policy” entry and click on “edit.

   ![Instruction5screenshot](/newblog/img/resources/2020-02-21-Post/5.jpg)

6. The “Group Policy Management Editor” window will show up. This screen allows us to edit the policy in any way that 
   we choose.
   
   ![Instruction6screenshot](/newblog/img/resources/2020-02-21-Post/6.jpg)

7. The first policy we will edit is connected to amount of days a password can be used. It is currently set to 42 days, 
   but we will be changing it to 60 days.

8. Go ahead and expand the folders to the left in this order, “Computer Configuration > Policies > Windows Settings > 
   Security Settings > Account Policies > Password Policy” once done you should see the available password policies.
   
   ![Instruction8screenshot](/newblog/img/resources/2020-02-21-Post/8.jpg)

9. Right click on “Maximum Password Age” and select “Properties”

   ![Instruction9screenshot](/newblog/img/resources/2020-02-21-Post/9.jpg)

10. On the properties window go ahead and change the days from 42 to 60 and click on “OK”.

    ![Instruction10screenshot](/newblog/img/resources/2020-02-21-Post/10.jpg)

11. That’s if you have now changed a computer-based group policy. Next we will change a user-based policy dealing with 
    screen savers. If the user leaves and the screen saver turns on upon returning we want the log in screen to instead 
    show. This helps in limiting unauthorized access.

12. Back at the “Group Policy Management Editor” expand the folders in this order, “User Configuration > 
    Administrative Template > Control Panel > Personalization” once down you should see the personalization options.
    
    ![Instruction12screenshot](/newblog/img/resources/2020-02-21-Post/12.jpg)

13. Right click on “Password Protect the Screen Saver” and select “Edit”.

    ![Instruction13screenshot](/newblog/img/resources/2020-02-21-Post/13.jpg)

14. On the setting window go ahead an enable the policy by selecting the “Enabled” radio button. Then click on “Okay”.

    ![Instruction14screenshot](/newblog/img/resources/2020-02-21-Post/14.jpg)

15. That’s it the user-based policy has now been applied. You can go ahead and close the Group Policy Management Editor” 
    window.

16. The last step is to link the policy to our user and computer containers. At the “Group Policy Management” window right 
    click on the computer container and then select “Link to existing GPO”.
    
    ![Instruction16screenshot](/newblog/img/resources/2020-02-21-Post/16.jpg)

17. On the “Select GPO” windows highlight the policy we edited which is “Default Domain Policy” and then click on “Okay”.

    ![Instruction17screenshot](/newblog/img/resources/2020-02-21-Post/17.jpg)

18. You should now notice that the Policies name is now showing under the computer container. Go ahead and do the same for 
    the user container.
    
    ![Instruction18screenshot](/newblog/img/resources/2020-02-21-Post/18.jpg)

Congratulations, the next step would be to add a workstation to the domain and test the policy. Which we will do later in a 
blog post dealing with setting up workstations and adding them to a domain. 
