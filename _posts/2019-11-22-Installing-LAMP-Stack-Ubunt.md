---
layout: post
title: "Installing a LAMP Stack on Ubunu"
date: 2019-11-22
categories: Blog
background: '/img/posts/08.jpeg'
---

Hi Everyone,

For this blog post I will be walking you through the process of installing a LAMP stack on Ubuntu. 

1. To begin you will need to make sure that you are running Ubuntu 18.04 or higher installed. As well make sure that the system is up to date by running the following command:

      - $sudo apt-get update

2. We will now being the installation of the necessary software; Starting with Apache. Run the first command to install Apache and then the second command to verify that it was installed correctly and running. 

      - $sudo apt-get install apache2
      - $sudo service apache2 status

3. Next, verify that the firewall has a profile for apache by running the first command and then make sure that you allow traffic to ports 80 and 443 by running the second command.

      -	$sudo ufw app list
      -	$sudo ufw app info “Apache Full”

4. Now we need to verify that apache is running correctly by going to a web browser and typing in the IP of the machine that has Ubuntu installed. If you are using a VM then you will need to most likely use the local host IP address with the port that you specified when you created the VM. IF you are using a server than you should be able to just use the servers IP address. You will see the page with the following heading:

      “Apache2 Ubuntu Default Page”

5. Next is the installation of MySQL which is used as a database. Run the following command to install MySQL and make sure to change the root password when prompted.

      - $sudo apt-get install mysql-server


6. After installing MySQL the next step is to install PHP using the following command:

      -	$sudo apt-get install php libapache2-mod-php php-mysql

7. In the next few steps we will verify that PHP was installed correctly. To do so we will first need to make a configuration change to Apache so that it serves up files with a PHP extension first rather than files with HTML extensions and we will also install some dependencies. Run the following command to open up the configuration file for editing:

      -	$sudo vim /etc/apache2/mods-enabled/dir.conf

      a. Within the file contents locate the section <IfModule mode_dir.c> and type index.php in front of the index.html it should look like this
          <IfModule mode_dir.c>
		DirectoryIndex index.php index.html index.cgi index.pl index.xhtml ind$
          </IfModule>

      Save the changes and exit out.

      b. Aside from installing PHP we will also need to install some PHP modules by running the following command:

      -	$ sudo apt-get install php-cli

8. Lastly, we will create a new file called index.php in the web root directory to test PHP. Run the following command to create the file:

      -	$sudo nano /var/www/html/info.php

      a. Type the following into the file:
        <?php 
          phpinfo ();
        ?>

      Save the changes and exit out.

9. Finally, it’s time to test the file we just created. Open a web browser and type in the following into your address bar:

      “IP address”/info.php

If you see a PHP information screen, then congratulations you have successfully installed a LAMP stack on an Ubuntu system. If you have issues, please contact me and I will be happy to help you out.

