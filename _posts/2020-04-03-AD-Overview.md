---
layout: post
title: "AD DS Overview on How The Domain Environment is Affected"
date: 2020-04-03
categories: Blog
background: '/img/posts/08.jpeg'
---

Hi Everyone,

For this week’s blog we will be reviewing the Active Directory installations as well as the workstations installation and how it all works together. We installed the following services Active Directory, DHCP, DNS, and a Print Server. 

## Active Directory

Starting with Active Directory we utilized the features Users and Computers and Group Policy management. When we added the workstation to the domain, changes occurred for these features. If we go back and check out the users and computers management console you will see an entry for the workstation in the computer’s container (Screenshot below). Whenever adding computers to the domain, the same will occur for each workstation. 

Image 1

Next, we used the group policy management to apply policies to the computers centrally from the domain controller. We can see these changes on the actual workstation by running a command window and using the command “gpresult /Scope Computer /v”. Thinking back to the post of group policies we edited the password age from 42 to 60 which you can see shows on the command window (Screenshot Below). 

Image 2



## DHCP
	
We also activated DHCP to give out IP addresses to all workstations on the network. If we bring up the DHCP management window we can see that the workstation that we added to the domain was served an IP address from the server (Top Screenshot). If we look at the workstation side and open a command prompt, then run the command “ipconfig /all” we see that under the “DHCP server” entry is the IP address of the domain controller (Bottom Screenshot).

Image 3

Image 4

## DNS
	
Like DHCP above DNS is also affected and the workstation is registered in DNS. If you open the DNS management window on the server, you should see an entry for the workstation computer (screenshot below). Having the entry saved in DNS allows you to look up computers on the network via their name instead of having to know the IP address.

Image 5

## Print Server

When it comes to printer management. The service allows you to add printers to computers via group policy but in case you want to add them manually if gives you the ability to add a specific printer by specifying the printer servers name then the printer name. If you go to add printer on the workstation then select the option for “Select a Shared Printer by Name” you can type in the server name, then a list of printers hosted by the print server will pop up (Screenshot below). This makes it easier to add a printer. Otherwise you would need to use the IP of the printer then have the drivers with you.  

Image 6


As you can see having an AD environment brings structure and organization. There is a big number of things that can be accomplished with an AD environment. I have only showed a very tiny portion of what can be accomplished. If you find yourself wanting to learn more make sure to conduct research online, you can even find free certification books online for Microsoft AD DS environments. 

