---
layout: post
title: "Installing Terraform on MacOS"
date: 2019-11-14
categories: Blog
background: '/img/posts/06.jpg'
---

Hi Everyone, 

For this blog post I will be walking you through the process of installing Terraform on a MacOS system.

1. To get started, navigate to the terraform downloads webpage and make sure to copy the link address for the MacOS download. The link is also below. 

   https://releases.hashicorp.com/terraform/0.12.13/terraform_0.12.13_darwin_amd64.zip

2. Next, open up a terminal window and navigate to the directory in which you would like to download the Terraform package. For my download I choose the home directory. Then run the following command to download the package (all one line):

   - $wget https://releases.hashicorp.com/terraform/0.12.13/terraform_0.12.13_darwin_amd64.zip

3. Once the download is complete the file will need to be unzipped and then moved into its on directory. Run the following command to unzip the file:

   - $unzip terraform_0.12.13_darwin_amd64.zip
   - $mkdir Terraform
   - $mv terraform Terraform/

4. Next, the path will need to be updated so that the Terraform binary can be called from anywhere on the system (e.g desktop, documents, home directories). On the home directory run the following commands to edit the .profile file:

   - $cd ~
   - $ls -al  (this command will display the contents of the home directory)
   - $vim ~/.profile	(you can use which ever text editor you would like)

5. Type in the following into your .profile file:

   export PATH=”$PATH:~/Terraform”

6. Next, you will need to update the path so that Terraform can be called from anywhere. To do so run the following command:

   - $source ~/.profile

7. Lastly to make sure that Terraform was installed correctly run the command below. It should return the Terraform version information:

   - $terraform –version

