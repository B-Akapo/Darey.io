# Introduction to LEMP Stack

Now that we have finished with our [LAMP Stack](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application), let us see how to deply a web application using the LEMP Stack. 

The LEMP stack stands as a powerful and widely-used infrastructure for web development and hosting. It's comprised of four key components:

- **Linux:** This open-source operating system forms the foundational layer of the stack, providing stability and security.
- **Nginx (pronounced as "Engine X"):** Serving as the web server, Nginx efficiently handles HTTP requests, making it a high-performance alternative to Apache.
- **MySQL (or MariaDB):** A robust relational database management system that manages and organizes structured data for applications.
- **PHP:** A popular server-side scripting language enabling dynamic content generation, interaction with databases, and the creation of web-based applications.

The combination of Linux, Nginx, MySQL, and PHP forms a robust environment for deploying scalable and high-performance web applications. Each component contributes uniquely to the stack, empowering developers with flexibility, security, and efficiency in web development and deployment.

Note that most of the processe are the same and I will be referring the the LAMP Stack document a lot. If you have yet gone through it, you can find it [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application)

# Getting Started With AWS
- **AWS Account:** Setting up an AWS account is actually vry easy. Everything you need to know can be found [here](https://aws.amazon.com/free/)
- **Setting Up an EC2 Instance: **I have a detailed step-by-step guide on how to set-up your EC2 instance on AWS. You can use [this docmentation](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#setting-up-an-ec2-instance) to quickly set yours up before coming back her to continue
- **Connecting To Your EC2 Instace:** In order to work remotely and effectively,you will need to connect your local machine to your EC2 instance. It is quite easy. I have a detailed step-by-step guide [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#connecting-to-your-ec2-instance-from-your-local-machine) on how to do that. DO that there and then we can continue with setting up our stack.

# Installing Nginx
Nginx, renowned for its efficiency and speed, serves as a powerful alternative to traditional web servers. Installing Nginx provides a foundation for serving web content, handling HTTP requests, and optimizing server performance.

**1. Update Package Lists:**
- Ensure your system's package list is up-to-date. run the command
```
sudo apt update; sudo apt upgrade
```
Remember to type `Y` when asked. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/package-update.png)

**2. Install Nginx:**
- Use apt to install the Nginx package.
```
sudo apt install nginx
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/install-nginx.png)

**3. Check Nginx Service Status**
- To confirm that Nginx is running as a service
```
sudo systemctl status nginx
```
Once you see green and active, you are good to go.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/check-status.png)

**4. Open TCP Port**

Port 80 is the default port for most web broswers. Lets quickly see how to open it. 
- Go back to "instances" on your AWS console.
- Click on security and then "security group". Please make sure you select the right instance

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/security-group.png) 

- In the "Security" page click on "Edit in0bound rules"
     
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/inbound-rules.png)

- click on **"Add rule"** set up the following:

  a. set "Type" to "HTTP"

  b. set "Protocol" to "TCP"
  C. set "Port range" to "80"
  d. set source to 0.0.0.0/0
  e. save rules
     
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/set-inbound-rules.png)

- Check Port In Local Machine, run the following command
```
curl http://localhost:80
```
or 
```
curl http://127.0.0.1:80
```
The two commands will give the same output which is the raw HTML code of the website. THe first command uses the `DNS name`. The second comand uses the `IP Address`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/port-80.png)

The two commands will give the same output which is the raw HTML code of the website. THe first command uses the `DNS name`. The second comand uses the `IP Address`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/port-80.png)

**5. Access Nginx Server On Browser**
- NOw instead of using the HTML file. Let's access the file on our browser. To get your IP run the following command
```
curl ifconfig.me
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/address.png)

- Or you can just go to your AWS console and scroll to the right and find your public IP address

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/address2.png)

- Once you have your IP you can just copy it into the browser or use `http://<Public-IP-Address>:80` and you should be able to access the site. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/nginx-page.png)

# Installing MySQL
Now that we have our sever running, the next step is to install a database management system. This allows you to store and manage data for your site. In the LAMP stack, the database management system used is MySQL. MySQL is a popular open-source relational database management system (RDBMS) renowned for its reliability, ease of use, and scalability. Developed by Oracle Corporation, MySQL is widely utilized for managing and organizing structured data.

**1. Install MySQL Server Package**
- To install the package use the command
```
# Install MySQL Server Package
sudo apt install mysql-server
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/install-package.png)

**2. Check Server Status**
- Now that it is installed, you can check the status to ensure it is running.
```
sudo systemctl status mysql
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/package-status.png)

Ideally, you package should be active and running. If it isn't, run the command
```
sudo systemctl start mysql
```

**3. Accessing MySQL**
- To access MySQL in the terminal, run the command
```
sudo mysql
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/access-mysql.png)

This command allows you to connect to MySQL shell as the administrative database root user.

**4. MySQL Security Configuration (Optional but Recommended)**

It is adviced that you run a pre-installed security script that comes with MySQL. This will help remove and insecure default setting and restrict access to your database
- Within the MySQL shell run the command
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY <'add your password here'>;
```
- exit the shell by typing `exit`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/sql-shell.png)

- Run the secure pre-installed script
```
sudo mysql_secure_installation
```
- You will be asked to validate password. Enter `y`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/password-validation.png)

- You now need to set your password, in accordance with the rules. You can choose and level you want `0`, `1`, or `2`. For this project I am going with 2. Note that any level you pick, you password must match.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/enter-password.png)

- From here on for any question you are asked. Simply enter `y`

**5. Test Password**
- Test if you can access MySQL with your new password. Run the command
```
sudo mysql -p
```
or 
```
sudo mysql -u root -p
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/test-password.png)

You should be able to access the shell now. No one can access your database without your password. 

# Installing PHP
As a web server, Apache incorporates a PHP interpreter directly into its architecture. This tight integration means that when Apache encounters a PHP file, it interprets and processes it internally, handling the server-side scripting without requiring an external helper. Contrastingly, Nginx treats PHP processing as an external task. It leverages an external program like PHP-FPM (PHP FastCGI Process Manager) to handle PHP script execution. This separation enables Nginx to focus on its core competency of efficiently serving static content while delegating the dynamic PHP execution to an external service, enhancing its scalability and performance.
```
sudo apt install php-fpm php-mysql
```
![Alt text]([install-php](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/install-php.png))

# Configure Nginx to Process PHP
Server blocks in Nginx serve a role akin to Apache's virtual hosts. They enable the configuration of multiple websites or applications on a single Nginx instance, allowing distinct sites to coexist and function independently. Let's begin.

**1: Create A Directory**
- To do this I will be naming my directory `myprofile`. You can name it what ever you want
```
sudo mkdir /var/www/myprofile
```
**2: Assign Ownership**
- Next thing we need to do is to assing ownership
```
sudo chown -R $USER:$USER /var/www/myprofile
```
- Set permissions using the `chmod` command
```
sudo chmod -R 755 /var/www
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/directory.png)

**3: Create A Server Block Configuration File**
- Create a blank configuration file using `vi`. Note you can use other editors like `nano` or `vs code`
```
sudo vi /etc/nginx/sites-available/myprofile
```
- while in `vi` take the following steps
* Hit `esc` key and the type `i`. This will take you to
* Copy the code below and paste in your editior
```
#/etc/nginx/sites-available/myprofile

server {
    listen 80;
    server_name myprofile www.myprofile;
    root /var/www/myprofile;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```
* Type `:` before typyin `wq` and hitting `ENTER`
* Not sure how exit `vi` watch this [video](https://www.youtube.com/watch?v=KwCvEVblJl8)

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/configure.png)

**4: Activate Configuration**
- You activate configuration by linking Nginx `sites-enabled` directory to the config file
```
sudo ln -s /etc/nginx/sites-available/myprofile /etc/nginx/sites-enabled/
```

**5: Test For Syntax Errors**
- To be sure your configuration file is error free, test for syntax errors using
```
sudo nginx -t
```
The out put you should see is 
`nginx: the configuration file /etc/nginx/nginx.conf syntax is ok`
`nginx: configuration file /etc/nginx/nginx.conf test is successful`

If there are any errors, simply go to your configuration file and edit. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/test.png)

**6: Disable Default Nginx Host**
```
sudo unlink /etc/nginx/sites-enabled/default
```
**7: Reload Nginx**
```
sudo systemctl reload nginx
```
YAYYY Your website is now active

**8: Create HTML File**
- To test your new server is working properly, create an `index.html` file
```
sudo echo 'Hello LEMP from hostname' $(curl -s http://51.20.74.243/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://51.20.74.243/latest/meta-data/public-ipv4) > /var/www/myprofile/index.html
```
Please remember to change the IP address to yours and also the directory

- Lets see if it works. Copy the following code into your browser
```
http://51.20.74.243:80
```
Remember to user your IP address

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/nginx.png)

You should see a similar page to the one above.

# Testing PHP With Nginx
Your LEMP Stack is fully set up and functional but you can test this to be sure

**1: Create a PHP File**
- use your choosen editor to create and `index.php` file . Will be use `vi`
```
vi /var/www/myprofile/info.php
```
- Copy the following code and paste in your editor
```
<?php
phpinfo();
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/php-file.png)
- save and exit
- Now if you enter you IP address and add your PHP file in your browser, you should see your PHP file
```
http://51.20.74.243/info.php
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/php-page.png)

- for saftey always delete your php file when you arent using it for maintenance as it containce delicate information. Doing this will revert to the original `index.html`
```
sudo rm /var/www/myprofile/info.php
```

# Retrieving Data From MySQL Database Using PHP
Now that our LEMP Stack is set up, let's dive in. We'll create a test database in MySQL, configure access, and execute queries to fetch and dynamically display data using PHP. This process highlights the seamless integration of Nginx, MySQL, and PHP within our LEMP environment, showcasing their collaborative strength in creating dynamic web experiences.

**1: Connect to MySQL**
- You connect to MySQL as a root user
```
sudo mysql -p
```
We are using `-p` here because we set the password earlier. 


**1: Create New Database**
- Within the SQL console, create a new database using the following command
```
mysql> CREATE DATABASE `example_database`;
```
The name of our database is `example_database`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/create-database.png)

**2: CReate New User**
- Now that you have the new database, create a new user
```
mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'your-choosen-password';
```
Remember to add your own secure password.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/create-user.png)

- Give new user permission over the new database
```
mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';
```
This will allow user to have access to a particular database but cannot create or modify access to other databases

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/grant-access.png)

- exit MySql
```
mysql> exit
```

**3: Test User Access**
- Now test to see if user does have access using customised user credentials
```
mysql -u example_user -p
```
When prompted, enter the password you created
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/grant-access.png)

- check to ensure that `example_user` has access to datatbase
```
mysql> SHOW DATABASES;
```

**4: Create Test Table**
- We will create a test table named `todo_list` in MySQL console
```
CREATE TABLE example_database.todo_list (item_id INT AUTO_INCREMENT,content VARCHAR(255),PRIMARY KEY(item_id));
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/create-table.png)

**4: Insert Values Into Table**
- Let's add some content into the table. You can do this as many times as you want to update new values to your table.
```
mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/create-list.png)

- Confirm that the data was successfully saved to your table
```
mysql>  SELECT * FROM example_database.todo_list;
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project4-deploying-LEMP-Application/images/show-table.png)

- exit MySql console
```
mysql> exit
```

**5: PHP Script To Connect TO MySQL**
- Create a new PHP file using your favourite text editor. I will be using `vi`
```
vi /var/www/projectLEMP/todo_list.php
```









  




