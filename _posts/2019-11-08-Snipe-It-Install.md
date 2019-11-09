---
layout: post
title: "Installing Snipe-It on Ubuntu"
date: 2019-11-08
categories: Blog
background: '/img/posts/06.jpg'
---

Hi Everyone,

For this post I will be walking you through the process of Installing Snipe-It Asset Manager on an AWS EC2 Ubuntu Instance.

1. In AWS create an EC2 Ubuntu instance. This is a rather simple process but if you have never created an EC2 instance please follow the link to a previous post where I walk you through the process:

     https://jjd90.github.io/newblog/blog/2019/10/24/Creating-an-EC2-Instance.html

2. Connect to the EC2 Instance via SSH or your preferred method. If you are using SSH over a terminal you command will looks something like this:

     ssh -i "newInstanceKey.pem" ubuntu@ec2-13-233-13-164.us-west-2.compute.amazonaws.com

3. Once you are connected to the EC2 instance go ahead and update the system then install Git (will be used to install Snipe_It) by running the following commands

     - sudo apt-get update
     - sudo apt-get -y upgrade
     - sudo apt-get -y install git

4. Next, Install Apache2 webserver, start it, and enable it by running the following commands:

     - sudo apt-get -y install apache2
     - sudo systemctl start apache2
     - sudo systemctl enable apache2

5. Next, Install PHP and its dependencies by running the following command:

     - sudo apt-get -y install php php-pdo php-mbstring php-tokenizer php-curl php-mysql php-ldap php-zip php-fileinfo php-gd php-dom php-mcrypt

6. Next, Is the installation of MariaDB which we will use to create our Snipe-It database. The following commands will install Maria DB, start MariaDB, and enable MariaDB:

     - sudo apt-get -y install mariadb-server
     - sudo systemctl start mysql
     - sudo systemctl enable mysql

7. Next, you will need to secure the MariaDB installation by running the command below, It will ask you to create a new root password, as well as give you the options to remove test database and remove any anonymous users.

     - sudo mysql_secure_installation

8. After securing Maria DB, log in to MariaDB using the new password you created in the step above and create a new database and user for Snipe-It. Run the following commands:

     Log In command:

          - mysql -u root -p

     Database and User creation commands:

          - CREATE DATABASE <snipeit DB Name>;
          - CREATE USER '< snipeituser name >'@'localhost' IDENTIFIED BY '< Password>';
          - GRANT ALL PRIVILEGES ON <snipeit DB Name>;.* TO '< snipeituser name >'@'localhost';
          - FLUSH PRIVILEGES;
          - EXIT;

               Note: Make sure to replace <snipeit DB Name> with 
               whatever you want to call the database, as well as 
               < snipeituser name > and < Password> with whichever 
               username and password you want.

9. The last piece of software to be installed, before Snipe-It, is Composer. Install it via the following commands:

     - cd ~
     - curl -sS https://getcomposer.org/installer | php
     - sudo mv composer.phar /usr/local/bin/composer

10. Now it’s time to install Snipe-It using Git (installed in the first step). Run the following commands:

     10a. First change into the webservers root directory via the command:

          - cd /var/www/

     10b. Second, Clone the Snipe-It repository for Github:

          - sudo git clone https://github.com/snipe/snipe-it snipe-it

11. Next, is the creation of the .env file for Snipe-It. The .env file is basically a configuration file that we will customize to reflect the server and database settings so that Snipe-It can run correctly. Run the following commands to change into the Snipe-It directory then create a new .env file:

     - cd /var/www/snipe-it
     - sudo cp .env.example .env

12. Next, Open the .env file and edit some of the contents. I use VIM text editor but feel free to use any editor of your choice. 

     - sudo vim .env

     Edit the following lines:

          APP_URL=null      	(Provide your domain or IP here, I used 
                                 my EC2 public IP)
          APP_TIMEZONE='UTC' 	(Change it according to your country)

          DB_DATABASE=null   	(Provide the database name you created 
                                 earlier)
          DB_USERNAME=null	Provide database user's username you 
                                 created earlier)
          DB_PASSWORD=null   	(Provide the DB user's password you 
                                 created earlier)

     Save your changes then exit the editor.

13. Next, the folder permissions and ownership for Snipe-It will need to be specified. The permissions will be set for the storage and public/uploads directories within the /var/www/snipe-it directory:

     - sudo chown -R www-data:www-data storage public/uploads
     - sudo chmod -R 755 storage
     - sudo chmod -R 755 public/uploads

14. Next, The installation of PHP dependencies using Composer is required. Run the following command from within the /var/www/snipe-it directory:

     - sudo composer install --no-dev --prefer-source

15. Next, is the process of generation and APP_KEY for Snipe-It to use. The following command will generate a new key and automatically paste it into the .env file:

     - sudo php artisan key:generate

16. For Snipe-It to work and be served up as a webpage, it is required to create a new virtual host file for apache. The following steps will make that happen:

     16a. Run the following command to create a new virtual file:

          - sudo vim /etc/apache2/sites-available/snipeit-hostfile.conf

     16b. Add the code below to the virtual file:

          <VirtualHost *:80>
  	     ServerName snipeit.example.com
   	     DocumentRoot /var/www/snipe-it/public
  	     <Directory /var/www/snipe-it/public>
        		Options Indexes FollowSymLinks MultiViews
        		AllowOverride All
        		Order allow,deny
       		allow from all
    	     </Directory>
          </VirtualHost>

     16c. Save and close the file then run the following commands to activate the host file and restart apache:

          - sudo a2ensite snipeit-hostfile.conf
          - sudo a2enmod rewrite
          - sudo systemctl restart apache2

17. Finally, we reach the end of the instllation. The next step is to connect to the IP/Domain that you set for your snipe-it installation. Upon doing that you will get to a preflight window which will allow you to finish the configuration through a web browser. You can either type in the IP address or the domain as shown below:

          http://snipeit.example.com or http://127.0.0.1 

     Congratulations you have now successfully installed snipe it on an EC2 instance!
