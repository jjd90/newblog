---
layout: post
title: "Active Directory Users and Computers"
date: 2020-02-14
categories: Blog
background: '/img/posts/04.jpg'
---

Hi Everyone,

Moving forward with the series of blog post focusing on AD DS we will be focusing on creating
Organizational Units also know as Containers and User accounts. When working in a windows environment
you will be asked to maintain containers and create user accounts.

Active Directory Users and Computers is the full name of the snap-in we will be using and if you took
a guess and concluded that it involves maintaining users, groups, and computers then you are correct.
The main purpose of AD Users and computers is to do just that. Below we will create some new containers
and a new network admin account as well as a regular non privileged user account that will be a member
of the Domain Users group and container.

1. Start by opening the “Active Directory Users and Computers” snap-in located under “Administrative Tools”.

   ![Instruction1screenshot](/newblog/img/resources/2020-02-14-Post/1.jpg)

2. Once opened you will notice a bunch of folders to the left. We will refer to these as containers. Notice
   that each container has a specific name and will server a specific purpose. Click on the “User” container
   to view all the users and groups.

   ![Instruction2screenshot](/newblog/img/resources/2020-02-14-Post/2.jpg)

3. Let’s start off by creating a new container for our unprivileged users. Right click on the name of your 
   domain then hover or “New” and select “Organizational Unit”.

   ![Instruction3screenshot](/newblog/img/resources/2020-02-14-Post/3.jpg)

4. At the “New Object Screen” type in the name you want. I will use “Acme Users” then click on “OK”.

   ![Instruction4screenshot](/newblog/img/resources/2020-02-14-Post/4.jpg)

5. Now we will create our domain admin account by copying directly from the built-in admin account which is
   the account we first create when we set up the server. Right click on the administrator entry and select
   “Copy…”.

   ![Instruction5screenshot](/newblog/img/resources/2020-02-14-Post/5.jpg)

6. The “Copy-Object User” window will appear and now you will need to type in a “first name”, which will
   populate the full name, and a “User Logon Name”. I used “acmeadmin” once done click “Next”.

   ![Instruction6screenshot](/newblog/img/resources/2020-02-14-Post/6.jpg)

7. Now we will create the password. Make sure to use a complex password for this account. Then click “Next” to
   go to the details overview window and finally click on “Finish”.

8. With the Domain admin account created let’s go ahead and create non privileged user. Start by clicking the
   “Create a new user icon at the top” (Red Box). Then on the window that pops up fill in the user’s information
   like we did for the admin account. I used “acmeuser”. Click “Next”, create a password then click “Next” again
   and finally click “Finish”.

   ![Instruction8screenshot](/newblog/img/resources/2020-02-14-Post/8.jpg)

9. The user account will automatically be added to the “Domain Users” group.

10. Next, we will need to add the domain user we created to the new container that was created in step 4. This is
    required so that we can later be able to apply group policies to the user. 

		Note: Group Policies will be covered in next week’s 
		blog post.

11. Right click on the domain user account that was created and then select “Move…”

    ![Instruction11screenshot](/newblog/img/resources/2020-02-14-Post/11.jpg)

12. On the window that pops go ahead and highlight the container that you created and then click on “OK”.

    ![Instruction12screenshot](/newblog/img/resources/2020-02-14-Post/12.jpg)

13. To confirm that the user was moved, Select the container and you should now see that the user you created is
    the only entry.

    ![Instruction13screenshot](/newblog/img/resources/2020-02-14-Post/13.jpg)

14. Lastly, lets create another one more container which will be used at a future time and will have all the
    organization’s computers in it. This will also be helpful with group policies.

15. Right click on the name of your domain then hover or “New” and select “Organizational Unit”. Then name the
    container, I used “Acme Computers”. Then click on “OK”.

    ![Instruction15screenshot](/newblog/img/resources/2020-02-14-Post/15.jpg)

Congratulations you have successfully accomplished creating a new domain admin, domain user, and two containers;
one for the users and one for the computers. Next week we will cover group policies and you will see why it was
helpful for us to create these accounts and containers.

