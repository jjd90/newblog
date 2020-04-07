---
layout: post
title: "AD DS Deploy Network Folder Using Group Policy"
date: 2020-04-10
categories: Blog
background: '/img/bg-post.jpg'
---

Hi Everyone,

Last week finished up the series of blog post on AD DS. We learned that in a Windows environment having 
a domain controller can bring structure and organization to your computer/server/network setup. This week 
we will continue with the Windows environment and I will show you how to map a shared network drive using 
AD DS group policy.

This is a cool feature because it allows you to share network folders with all or specified user groups. 
In my time if seen network shares deployments used to deliver important documentation to users such as, 
department files, policies & procedures, and other job-related files. We will start by creating a network 
share folder and then setting up the group policy. 


1. Open a Windows Explore window and navigate to the location where you want to create the folder.

       Note: When setting up network shares I usually create 
       a separated partition on the desk just to store files 
       but for this tutorial I will be using the same partition 
       that as the OS also known as the C: drive.

2. Once you’re at the location you feel is best go ahead and select new folder from the top tool bar. 
   This will create a new folder that you can name however you like. I will be using the name “Public” 
   to denote that it is a public folder.

3. Next, we want to set it as a network share folder. Go ahead and Right Click on the folder and click on 
   “Properties” and then on the properties window select the “Share” Tab and then click on the “Share…” button.

4. On the file sharing window go ahead and click on the “Arrow” to the left on the greyed out “Add” button. 
   Then select “Find People”.

5. The “Select Users or Groups” window will pop up. Go ahead and type in “domain users” in the empty box and 
   then click on the “Check Names” button. This will retrieve the domain users’ group and link it to this shared 
   folder. Lastly, click on “Okay” to exit the window.

6. Back at the “File Share” window you should now see a domain user’ entry. To activate the sharing click on the 
   “Share” button. The folder should now be accessible via a network share.

7. We will now test to make sure the folder is available over the network. Go ahead and open a new Windows Explorer 
   window and then navigate to the server share by typing in the following address “\\<server name>\”. If successful 
   you should see the folder that you shared. 

8. We can not create the group policy to deploy the folder. Go ahead and open the “Group Policy Management” window. I 
   will use the existing group policy, but you can create a new one. Right click on the group policy name and then 
   select “Edit…”.

9. The “Group Policy Management Editor” will open. Go ahead and navigate the to the following section, “User 
   Configuration > Preferences > Windows Settings > Drive Maps”.

10. Next, right click on “Drive Maps”, select “New”, and then click on “Mapped Drive”.

11. The “New Drive Properties” window will pop up. Go ahead and fill out the information below. When done click 
    on “Ok”.

     -	Action:	 Select “Update”.
     -	Location: “\\<server name>\ Share folder” (e.g. \\acme-pdc\Public ).
     -	Reconnect:  Make sure it is selected.
     -	Label As: This will be the name that shows up for users.
     -	Drive Letter:  Choose the letter you want.

12. Back at the “Group Policy Management Editor” you should now see the drive entry and a green icon next to the name.

13. That’s it for the group policy. Now we need to test to make sure that it works. Turn on your workstation and log 
    into to a domain user account. Open a Windows Explorer window and navigate to “My PC”. You should now see the folder 
    that we mapped using the group policy. 

        Note: It might take a while for the policy to transfer 
        over to the workstation. If at first you don’t see it, 
        restart  your computer 2 to 3 times before troubleshooting. 
        You can also run the command “gpupdate /force” in a command 
        prompt.

If everything checks out then congratulations, you have successfully set up a network shared folder and deployed it 
using a group policy. If you experience any issues check your deployment settings again and make sure that you are 
logged in with a domain user account. You can also reach out to me for help. Until next week…


