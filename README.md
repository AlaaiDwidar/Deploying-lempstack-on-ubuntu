# Deploying-lempstack-on-ubuntu

## Step 1 – Installing the Nginx Web Server
`sudo apt update`

`sudo apt install nginx`

Go to your browser http://server_domain_or_IP

to edit in your website 

1)Go to etc/var/www/html/index.nginx-debian.html

(/var/www/html/: This is the root directory for the default website served by Nginx)

(index.html file and other web content for the default website are typically stored here)


2)Edit and save your changes

![image](https://github.com/AlaaiDwidar/Deploying-lempstack-on-ubuntu/assets/99266660/96f7c276-eb5f-4ddc-b1fc-9924d2a56210)

## Step 2 — Installing MySQL

`sudo apt install mysql-server`

`sudo mysql_secure_installation`

When you’re finished, test if you’re able to log in to the MySQL console:

`sudo mysql`

then `exit` after test

## Step 3 – Installing PHP

`sudo apt install php8.1-fpm php-mysql`

## Step 4 — Configuring Nginx to Use the PHP Processor

`1)cd  /var/www/html/`

`2)vim index.html`

and put the content of your website

<html>
  <head>
    <title>your_domain website</title>
  </head>
  <body>
    <h1>Hello World!</h1>

    <p>This is the landing page of <strong>your_domain</strong>.</p>
  </body>
</html>

 3)Reload nginx

`systemctl restart nginx`

![image](https://github.com/AlaaiDwidar/Deploying-lempstack-on-ubuntu/assets/99266660/54a3d08f-b2bb-4ee4-ab75-8034b28c55de)

 ## Step 5 –Testing PHP with Nginx
`1)cd  /var/www/html/`
 2)vim info.php 
 and put this content
` <?php
phpinfo();'

![image](https://github.com/AlaaiDwidar/Deploying-lempstack-on-ubuntu/assets/99266660/e106fb15-f04b-4529-b99f-1aaf060eff16) 
## Step 6 — Testing Database Connection from PHP

`sudo mysql -uroot -p`

`CREATE DATABASE php_database;`

`CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';`

`GRANT ALL ON php_database.* TO 'example_user'@'%';`

`CREATE TABLE Php_database.todo_list (
	item_id INT AUTO_INCREMENT,
	content VARCHAR(255),
	PRIMARY KEY(item_id)
);`

`exit`

`sudo vim /var/www/html/todo_list.php`

put your database info:

from this file database_php


test youdatabase

`http://server_domain_or_IP/todo_list.php`





![image](https://github.com/AlaaiDwidar/Deploying-lempstack-on-ubuntu/assets/99266660/6cf5c4a5-75de-4d12-8674-7081f1be82bc)



















































