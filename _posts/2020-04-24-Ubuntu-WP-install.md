---
layout: post
title: "Install WordPress on an Ubuntu 18.04 server"
date: 2020-04-24
categories: Blog
background: '/img/bg-post.jpg'
---

Hi Everyone,

Welcome back to my CIT blog. This week we will step away from the windows environment and I will walk you through 
the process of installing WordPress on an Ubuntu 18.04 LTS server. WordPress is a powerful tool used to create 
websites all around the world. It is one of the more popular website creation tools and the cool thing is that it 
is free. 

In this scenario I have set up an EC2 (virtual machine) in AWS and installed Ubuntu Server 18.04 LTS. You can use a 
virtual server as well or a physical one. I will leave that choice up to you. 

1. To get started will need to log into the ubuntu server and update the OS, to do so run the following command:

       apt update && apt upgrade

2. After updating the OS we will need to install apache2. Run the following command to install apache:

       apt install apache2

3. After the install of apache2 is complete we need to test the install. To check if the apache2 service is running 
   run the following command:

       systemctl status apache2

4. You can also make sure that apache2 is installed correctly by going to the server ip address on a web browser. 

       http://<IP Address> 

5. Next, we will need to install MySQL. We will be using the MariaDB variant for this tutorial. Run the following command 
   to install MariaDB.

       apt install mariadb-server mariadb-client

6. Once MariaDB is installed, we will need to secure the installation by running the following command:

       mysql_secure_installation

7. Upon running the command, you will be asked for the root account password. In our case it is blank so go ahead and 
   just press enter to proceed. You will then be asked to create a new root password.

8. After setting a root password you will be asked if you want to remove anonymous users. Go ahead and enter “Y” for yes.

9. Next, you will be asked if you want to disallow root login remotely. For our purpose we don’t need to disallow it, so 
   you enter “N” for no.

10. Next, you will be asked if you want to remove the test database. Enter “Y” for yes.

11. Next, you will be asked if you want to reload the privilege tables. Enter “Y” for yes. 

12. Now, we will need to install PHP. To do so run the following command:

        apt install php php-mysql

13. Worpress will need a database so we will create one now. Run the following command to create a database:

        mysql -u root -p

14. You will be taken into the mariadb console, to initiate the creation run the command:

        CREATE DATABASE wordpress_db;

15. Next, we will need to create the database user account. Run the following command:

        CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'password';

16. We will now need to grate privileges for the new user. Run the command:

        GRANT ALL ON wordpress_db.* TO 'wp_user'@'localhost' IDENTIFIED BY 'password';

17. Lastly for the DB creation we will need to flush the privileges and then you can exit by running the following 
    commands:

        FLUSH PRIVILEGES;
        EXIT;

18. Now its time for the good part, the installation of wordpress. We will download the wordpress files to the temp 
    folder by running the following commands:
    
        cd /tmp
        wget https://wordpress.org/latest.tar.gz

19. Next we need to uncompress the tar.gz we just downloaded by running the following command:

        tar -xvf latest.tar.gz

20. Now we will need to copy the wordpress files into the /var/www/html/ directory by running the following command:

        cp -R wordpress /var/www/html/

21. Then we will need to change the ownership of the folder that we copied as well as the permissions by running the 
    following commands:

        chown -R www-data:www-data /var/www/html/wordpress/
        chmod -R 755 /var/www/html/wordpress/

22. After changing the permission and ownership we need to create a directory for our uploads. Then we need to also 
    change the permissions for the directory. To do so run the following commands:

        mkdir /var/www/html/wordpress/wp-content/uploads
        chown -R www-data:www-data /var/www/html/wordpress/wp-content/uploads/

23. We will now need to finish the install of wordpress using a browser. To do so navigate to the following directory on 
    your web browser:

        https://<server ip>/wordpress

24. Select your language preference and then select “continue” to go to the “Getting Started” page. After reading the info
    go ahead and select “Let’s Go!”.

25. Now, you will need to enter the database information that we created previously. Enter the details and then select 
    “Submit”. Now you will be asked to run the wordpress installation, click on “Run the installation” to continue.

26. You will be taken to another screen where you will create the admin wordpress account. Enter the details and then 
    click on “Install WordPress”.

27. If everything is done correctly then you will see a success message. Click on “Log In” to get taken to the wordpress 
    dashboard.

Congratulations you have successfully installed wordpress on an Ubuntu server. If you have any issues getting the install 
completed feel free to contact me for help. Thanks for reading!
