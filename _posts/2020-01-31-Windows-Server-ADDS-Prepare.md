

Hi Everyone,

Welcome back to my blog post tutorials. For the next couple of blogs, I will be focusing on the
Microsoft Windows environment. I will be creating a series of post that will focus on implementing
Active Directory Domain Services (AD DS) and components such as DNS, DCHP, and any other service that 
might be connected to AD DS. This blog post will focus on creating a lab environment and installing 
Windows server 2016. With that being said let’s get started. 

1.	Choosing your environment:

For these purposes I will be using a virtual environment but please be aware that AD DS would be better if installed on a physical server. If you can get your hands on a such server great; otherwise a virtual environment will be fine. I will be using virtual box, but you can use any hypervisor that you would like.

2.	Now that we are ready to officially start go ahead and create a bootable disk/usb with Windows Server 2016. WS 2016 can be acquired from Microsoft as an evaluation copy that can later be activated (I recommend rufus to create bootable usb drives). If using a virtual environment go ahead and attach the WS 2016 ISO file and boot up from it. 

3.	Once booted up at the start up screen leave the default settings and click on “Next” and then “Install Now”

4.	At the OS selection menu make sure to select “Windows Server 2016 Standard Evaluation (Desktop Experience)” then click “Next”. Note: we will not be using a server core installation due to the complexity of set up. 

5.	Accept the licensing terms and then click “Next”

6.	At the Installation Type Window select “Custom: Install Windows Only (Advanced)”

7.	Now select the drive on which you want to install Windows Server then click on “Next”

8.	Windows will go through the installation process and your server might restart a few times during the process.

9.	Once windows has finished installing you will be prompted to create an administrator password. I recommend you use a complex password.

10.	You should now be at the log in screen. We will sign in and make some changes to the server in order to prepare it for the installation of Active Directory Domain Services which, will be covered in the next blog post.

11.	Log in and let’s start by changing the server name. This is a necessary step as the server is assigned a random name and in it will make is easier on us to identify this server once the domain environment is up and not to mention that this server will act as the primary domain controller.

12.	On the taskbar at the bottom click on the folder icon to open up a windows explorer window. To the left you will see an entry names “This PC” right click on it and select “properties” and then the system window ill be displayed.

13.	In the system windows under the section named “Computer name, domain, and workgroup settings” select “Change settings” which is to the right.

14.	The “System Properties” window will be displayed, select the button labeled “Change”.

15.	In the field right under “Computer name:” type in the name that you would like to give the server. Then click “Okay” to close the window then restart the server for the changes to take effect.

Note: I will go with a naming convention that is often used and places the name of the site/organization at the beginning and then PDC afterwards which indicates that the server is a Primary Domain Controller. It is displayed as “Acme-PDC”. 

16.	The next step is to assign a static IP address to the server. Since it will act as a primary domain controller it is a very good idea to give it a static address that neve changes so that once the domain environment is up it wont cause issues with services such as DNS. 

17.	To get to the network settings go ahead an click on the windows icon to the bottom left and then type “Control Panel” then click on the control panel Icon to bring up the control panel window.

18.	Click on the “Network and Internet” link, the non the next window click on the “Network and Sharing Center” link. 

19.	On the network and sharing center window click on the “ethernet” link which is to the right of the page right next to “connections:”; this will launch the “Ethernet Status” window. On this window click on the “Properties” button.

20.	The “Ethernet Properties” window will now show. Highlight the field that is named “Internet Protocol Version 4 (TCP/IPv4)” and then select the “Properties” button.

Note: Before proceeding make sure that you have identified the static IP address that you will be assigning to the server. You can leave the DNS server setting as is for the meantime but be aware that once we create the domain and activate AD DS the DNS addresses will change. (This will be covered on the next blog post as well)

21.	On the --- screen go ahead and type in the IP address that you will be using. Make sure to also include the subnet mask and the gateway IP address. Go ahead and leave the DNS option to automatic for now then click on the “okay” button to exit.


Congratulations you have installed Windows Server 2016 Desktop Experience and made the proper configuration to prepare it for the installation of the Active Directory Domain Services Role. On the blog post for next week we will go through the steps of for creating and domain and initiating the Active Directory Domain Services Role

Thank You!
