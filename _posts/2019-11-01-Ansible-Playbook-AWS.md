---
layout: post
title: "Install Ansible on Ubuntu and Run Playbook Againts AWS Instance"
date: 2019-11-01
categories: Blog
background: '/img/posts/04.jpg'
---

Hi Everyone,
For this blog post I will be walking you though the process of installing Ansible on ubuntu and then running the Ansible playbook against an Amazon Web Services EC2 instance.

1. In an Ubuntu terminal type in the following commands to install ansible:

      -	$ sudo apt update
      -	$ sudo apt install software-properties-common
      -	$ sudo apt-add-repository --yes --update ppa:ansible/ansible
      -	$ sudo apt install ansible

      1a. To make sure that ansible was installed correctly run the following command:
   
          - $ ansible --version

2. Next will be the installation of the AWS CLI application which will give us the ability to run the playbooks without having to log in or specifying credentials in our Ansible file (more secure).

      2a. We will be using pip to install aws cli so make sure it is installed by running the following command:
          - $ pip –version
 
          If pip is not installed run the following commands: 
		
          Pip2
               - $ sudo apt install python-pip
          Pip3
               - $ sudo apt install python3-pip

      2b. Run the following command to run the AWS CLI install:
	
          Pip2
               - $ pip2 install awscli --upgrade –user
          Pip3
               - $ pip3 install awscli --upgrade –user

      2c. To make sure that AWS CLI was installed run the following command:
 
          - $ aws –version

3. Next, we will need to generate access keys for the IAM user which you will be using to connect to the EC2 instance. You can generate those keys by going to the IAM section in AWS then going into users and selecting the desired user and lastly going into the “Security Credentials” section and clicking “Create Access Keys”. Make note of the ID and Secret. 

4. Now back at the terminal run the following command:

       - $ aws configure

             You will be asked for the following information:
             AWS Access Key ID: <enter key>
             AWS Secret Access Key: <enter key>
             Default region name: <can be any region I used us-west-2>
             Default output format: json

5. We will now go back to ansible and configure the host (Inventory) file with the information of the instance that we will want to run the Ansible playbook against. 

        Note: create an AWS EC2 instance running Ubuntu manually. There
              are methods to automate the provisioning of EC2 instances
              but for simplicity create it manually. Also make sure to
              save the keypair file which we will also need and that
              in the security group you open ports 22, 80, and 443 as
              we will be installing apache2 using ansible.

      5a. Navigate to the following directory “/etc/ansible/” If the directory does not exist create it. Inside of that 
          directory there should be a host file if not create the host file using you favorite cli editor (I use vim) 
          and then type in the following:

      -[aws]
      -<Public IP of EC2> ansible_user=ubuntu ansible_ssh_private_key_file=<location .pem file>

      -Example:
      -0.0.0.0 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/keypair.pem

      5b. To verify that the inventory is pulled correctly run the following command:
       
          - ansible all --list-hosts

6. Now that the inventory file is ready, create a simple Ansible playbook and make sure to specify the host and aws. My playbook looks like this (playbook.yml):

       -       ---
       -       - hosts: aws
       -	 tasks:
       -	     - name: install apache2
       -	       become: true
       -	       apt:
       -                  name: apache2
       -                  state: latest
       -                  force_apt_get: yes
       -	
       -             - name: start apache2 service
       -	       service:
       -	             name: apache2
       -	             state: started

7. Now is the moment of truth, type in the following command within the directory that you have your ansible playbook in:

          - ansible-playbook playbook.yml

8. If all went well, you should see the ansible output and then completion message. Congratulations you have successfully ran an Ansible playbook against an AWS EC2 instance. If you run into any issues, please contact me or run a google search on your error message. Google works wonders!
