---
layout: post
title: "Setting up a DHCP Server and DNS For an Active Directory Environment"
date: 2020-02-28
categories: Blog
background: '/img/posts/04.jpg'
---

Hi Everyone,
	
Now that we have setup up Active Directory, created users, and group policies. We can begin preparing the 
domain controller to handle some networking task. Usually for smaller organizations the Domain Controllers 
will host DCHP and DNS servers to help handle network traffic. In large organizations the DCHP and DNS servers 
will usually be installed on separate servers so that they can handle high traffic but for our purposes we will 
stick with an all in one solution.
	
We will first install and then set up a DHCP server role with will then activate the DNS server.

1. To install the DHCP role start by going to “Manage” and then selecting “Add Role and Feature” in the Server 
   Manager window.
   
   ![Instruction1screenshot](/newblog/img/resources/2020-02-28-Post/1.jpg)

2. Next on the “Add Roles and Feature Wizard” windows select “next” at the bottom.

   ![Instruction2screenshot](/newblog/img/resources/2020-02-28-Post/2.jpg)

3. Under the “Installation Type” section leave the default on “Role-based of feature-based installation” and the 
   click “Next”.

   ![Instruction3screenshot](/newblog/img/resources/2020-02-28-Post/3.jpg)

4. Next on the “Server Selection” section leave the defaults and then click on “next”

5. Now, on the “Server Roles” section you will need to check off “DHCP”, doing so will pop up a “Add Features” 
   pop up window. Leave the defaults for that windows and click on “Add Feature”. You will be taken to the 
   previous window where you will see “DHCP” checked off. Go ahead and click “Next”.
   
   ![Instruction5screenshot](/newblog/img/resources/2020-02-28-Post/5.jpg)

6. On the next section called “Features” leave the defaults and click on “Next”. Do the same for the next 
   sections called “DHCP Server”.

7. Finally, at the confirmation section. Look over the settings you choose, make sure everything looks good and 
   then click on “Install”.
   
   ![Instruction7screenshot](/newblog/img/resources/2020-02-28-Post/7.jpg)

8. The installation will take a few minutes to complete. Once done click on “Close”

9. Now that we have the DHCP role installed let’s go ahead and configure it. At the server manager window, you 
   should now notice a caution sign at the top right. Click the caution sign and then select the link that says 
   “Complete DHCP Configuration”.
   
   ![Instruction9screenshot](/newblog/img/resources/2020-02-28-Post/9.jpg)

10. You will now see the “DHCP Post-Install configuration wizard” window. The window gives details on what will 
    be accomplished through the wizard. In this case the security groups for the service will be created. Go 
    ahead and click on “Next”.
    
    ![Instruction10screenshot](/newblog/img/resources/2020-02-28-Post/10.jpg)

11. On the “Authorization” section leave the default of “Use the following user’s credentials” and then click 
    on “Commit”.
    
    ![Instruction11screenshot](/newblog/img/resources/2020-02-28-Post/11.jpg)

12. On the “Summary” section go ahead and click on “Close”.

13. We are not quite down yet. The last thing to do is create a scope of addresses that the server will give out 
    to workstations. Start by opening the “DHCP” snap-in located under “Administrative Tools”.
    
    ![Instruction13screenshot](/newblog/img/resources/2020-02-28-Post/13.jpg)

14. On the “DHCP” snap-in window to the left you will need to expand the entry that shows your domain controller 
    name and domain name. This will uncover a “IPv4” and “IPv6” option. Highlight the “IPv4” to show the 
    “Add Scope” message.

        Note: for this tutorial we will not be using IPv6.
	
    ![Instruction14screenshot](/newblog/img/resources/2020-02-28-Post/14.jpg)

15. Now right click on the “IPv4” entry and select the “New Scope” option.

    ![Instruction15screenshot](/newblog/img/resources/2020-02-28-Post/15.jpg)

16. You will now see the “New Scope Wizard” window. Go ahead and click on “Next”.

    ![Instruction16screenshot](/newblog/img/resources/2020-02-28-Post/16.jpg)

17. On the next windows you will need to provide a scope name. To keep it simple I will use “acmev4scope” but 
    you can you whatever you like. Then click on “Next”.
    
    ![Instruction17screenshot](/newblog/img/resources/2020-02-28-Post/17.jpg)

18. Now you will see the “IP Address Range” section you will need to enter some IP addresses for the server to 
    hand out. I will be using a class C range of only 20 addresses and a subnet of 24 (See screenshot for 
    details). When done click on “Next”

        Note: This is something that you will need to think about and will need 
              to take the size of the organization into account. This is a simple
              tutorial so we will be using a small range of addresses. 

    ![Instruction18screenshot](/newblog/img/resources/2020-02-28-Post/18.jpg)

19. On the next window “Exclusions..” leave everything as is and click on “Next”. We will not be excluding 
    any IP addresses in the range that we specified for this tutorial.

20. The next window deals with the lease duration for the IP address. Go ahead and leave the default of 8 
    days then click on “Next”.
    
    ![Instruction20screenshot](/newblog/img/resources/2020-02-28-Post/20.jpg)

21. Now you will see the section for “Configure DHCP Options”. We want to leave the default of yes. In the 
    next few steps we will be specifying the IP address information for the gateway (router) and other options
    that will be given to workstations. Click “Next”.
    
    ![Instruction21screenshot](/newblog/img/resources/2020-02-28-Post/21.jpg)

22. For the Router entry go ahead and enter your gateway address. Then click on “Add” then click on “Next”.

    ![Instruction22screenshot](/newblog/img/resources/2020-02-28-Post/22.jpg)

23. On the next window called “Domain Name and DNS servers” leave the defaults and then click on “Next”. On the 
    “WINS Server” section also leave it alone and click on “Next”.

        Note: Under DNS entry we left the default because we will be using the 
              domain controller as a DNS server. In the real world you could 
              include a backup serve address such as the one provided by your 
              ISP for redundancy. If your DC would go down, then staff would 
              still be able to get out to the internet.

24. Finally, you should be at the “Activate Scope” window. Leave the default of “Yes, I want to activate this 
    scope now” and click on “Next”
    
    ![Instruction25screenshot](/newblog/img/resources/2020-02-28-Post/25.jpg)

25. Now click on “Finish”. 

26. Back at the “DHCP” window you will now see more details to the left. If you go to the “Address Pool” entry 
    you will not see that range of IP addresses that we specified for the server to give out. Once we add a 
    workstation to the network you will see it show up under the “Address Leases” section.

        Note: DNS server will begin going to work as soon as we activate the 
              scope and get computer on the network. For this environment we 
              don’t have to make any changes to the DNS server settings. 
	      
    ![Instruction26screenshot](/newblog/img/resources/2020-02-28-Post/26.jpg)

Congratulations you have now successfully added a DHCP server to a domain controller. You will see the fruits of 
this labor once we add a workstation to the network, which we will in one of the next blog post.

