# Introduction to LAMP Stack

The LAMP stack, an acronym for Linux, Apache, MySQL, and PHP/Perl/Python, represents a foundational setup widely utilized for web development and hosting dynamic web applications. Each component plays a crucial role:

- **Linux:** This open-source operating system forms the stable base for the entire stack, providing flexibility and security in web server environments.
- **Apache:** Serving as the web server software, Apache handles HTTP requests, allowing your system to deliver web content efficiently.
- **MySQL:** It's a robust relational database management system (or alternative databases like MariaDB) crucial for storing and managing the application's data.
- **PHP/Perl/Python:** These scripting languages facilitate the development of dynamic web pages, enabling interaction with the server and database to generate dynamic content.

The synergy between these components forms a powerful environment for web application development and deployment, offering a solid foundation for hosting various online projects.

# Getting Started with AWS
The first step to deploying your LAMP stack application is understanding Linux and how to navigate it, if you are new to Linux, there are several beginner friendly videos. Additionally, I share a project on linux commands that you can go through [here](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands)

The second step is to set up you AWS account. Amazon Web Services (AWS) is a comprehensive and highly versatile cloud computing platform offered by Amazon. It provides a wide array of cloud services, including computing power, storage options, networking capabilities, databases, machine learning, analytics, and more. AWS allows businesses and developers to access scalable and flexible cloud infrastructure on a pay-as-you-go basis, eliminating the need for owning physical hardware. This cloud platform empowers organizations of all sizes to build sophisticated applications, host websites, store data, and leverage advanced technologies without the overhead costs and complexities of managing physical servers.

## Signing Up for AWS

To get started with Amazon Web Services (AWS), you can sign up for an AWS account [here](https://aws.amazon.com/free/). Follow the on-screen instructions to create your account.

## Setting Up an EC2 Instance:

**1. Launching an EC2 Instance:**
   - Log in to your AWS Management Console.
   - Navigate to the EC2 service.
   - Click on "Launch Instance" to create a new virtual server (EC2 instance).

**2. Choosing an Amazon Machine Image (AMI):**
   - Select an AMI based on your requirements (e.g., Amazon Linux, Ubuntu, etc.).

**3. Selecting an Instance Type:**
   - Choose the instance type based on your computing needs (e.g., t2.micro, t3.large, etc.).

**4. Configuring Instance Details:**
   - Set instance details like the number of instances, network settings, etc.

**5. Adding Storage:**
   - Define the storage requirements for your instance (e.g., size, type).

**6. Configuring Security Group:**
   - Create or select a security group to control traffic to your instance (e.g., SSH, HTTP, etc.).

**7. Review and Launch:**
   - Review your configuration settings and click "Launch."

**8. Connecting to Your Instance:**
   - Use SSH to connect to your instance using the provided public IP address.

For detailed step-by-step instructions on setting up an EC2 instance, refer to the AWS documentation [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html). Or you can watch [this](https://www.youtube.com/watch?v=osqZnijkhtE&t=5s) beginner friendly video.

# Connecting To Your EC2 Instance From Your Local Machine
Now that you have your EC2 instance running, let's access it from your local machine. 

**1. Open Terminal**
- On Linux OS, open the terminal application. use the shortcut `Ctrl + Alt + T`.

**2. Navigate to the Directory Where the PEM Key is Stored**
- while setting up the keypair for your intance on AWS, you downloaded a `.pem` file. Usually, it will be in the download folder. I will advice that you move it to another directory. In my own case I am putting it in `~/study/lamp-practice`. You can run the `ls` command to make sure it is there

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/pem-file.png)

3. Set Permissions for the PEM Key
- Set appropriate permissions to the key file. The syntaxt is
 ```
# Set Permission
 chmod 400 <your-key>.pem
 ```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/pem-permission.png)  

Dont worry if you don't see anything on the screen. It means it worked. `chmod 400` sets the permissions so that only the owner of the file has read access, while all other users (group and others) have no permissions to read, write, or execute the file. To see if your permission is set run the comman `ls -al` on your terminal 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/check-pem-permission.png) 

**4. Connect To EC2 Using SSH**
- In the terminal, use SSH to connect to your EC2 instance using the syntax
```
# Connect to EC2 instance
ssh -i /path/to/your-key.pem ec2-user@your-ec2-public-ip
```
Dont worry if you dont remeber it. It is easy to get.
   * First got to your AWS console and go to `instances`
   * MAke sure the instance you want is selected and the click on `connect`
     
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/instance-check.png) 

   * While in connection dashboard, go to `SSH Client`, copy the whole code under "Example" and paste in your terminal and hit enter. You'll see a command line prompt for your instance, indicating a successful connection.
     
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/client-ssh.png) 

And that's it, you are now connected to your EC2 instance on your local machine. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/connected.png) 

# Installing Apache
Now that we have our instance running on our local machine it is time to install Apache

Apache HTTP Server, commonly known as Apache, is one of the most widely used open-source web server software globally. It's renowned for its reliability, flexibility, and robust performance in serving web content. It is the go-to choice for hosting websites, serving web applications, and managing web content due to its stability, versatility, and extensive community support.

**1. Update and Upgrade Package Lists**
- Update the package lists to ensure you have the latest information about available packages
```
# Update package list
sudo apt upgrade

# Upgrade package list
sudo apt upgrade
```
Better still you can run the two at once by using `sudo apt update && sudo apt upgrade -y`. The why stands for yes and just means you want to go ahead with the upgrade

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/upgrade-package.png) 

**2. Install Apache**
- Install the Apache package using `apt`
```
# Install Apache
sudo apt install apache2
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/install-apache.png) 

**3. Check Apache Service Status**
- To confirm that Apache is running as a service
```
# Check apache service
sudo systemctl status apache2
```
Once you see green and active, you are good to go. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/apache-service.png) 

**4. Open TCP port 80**

Port 80 is the default port web browsers use to access web pages.
   * Go back to "instances" on your AWS console.
   * Click on security and then "security group". Please make sure you select the right instance
     
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/security-group.png) 

   * In the "Security" page click on "Edit in0bound rules"
     
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/inbound-rules.png)

   * click on **"Add rule"** set up the following:

      a. set "Type" to "HTTP"

      b. set "Protocol" to "TCP"

      C. set "Port range" to "80"

      d. set source to 0.0.0.0/0

      e. save rules
     
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/set-inbound-rules.png)

**5. Check Port In Local Machine**
- To ensure you have access to the port, run the following command
```
$ curl http://localhost:80
```
or 
```
$ curl http://127.0.0.1:80
```
The two commands will give the same output which is the raw HTML code of the website. THe first command uses the `DNS name`. The second comand uses the `IP Address`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/port-80.png)

**6. Access Apache Server On Browser**

NOw instead of using the HTML file. Let's access the file on our browser
- To get your IP run the following command
```
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
```
or run
```
curl ifconfig.me
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/address.png)

- Or you can just go to your AWS console and scroll to the right and find your public IP address

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/address2.png)

- Once you have your IP you can just copy it into the browser or use `http://<Public-IP-Address>:80` and you should be able to access the site. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/apache-page.png)

**7. Managing Apache**
- To start, stop, or restart Apache, use these commands:
```
sudo systemctl start apache2     # Start Apache
sudo systemctl stop apache2      # Stop Apache
sudo systemctl restart apache2   # Restart Apache
```

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
PHP (Hypertext Preprocessor) is a widely used open-source scripting language specifically designed for web development. Initially created by Rasmus Lerdorf in 1994, PHP has evolved into a versatile language powering numerous websites and web applications. PHP is commonly used for tasks like processing form data, interacting with databases, generating dynamic page content, and creating web-based applications.

**1. Install PHP and Related Packages**
- Install PHP and necessary extensions for common web development
```
sudo apt install php libapache2-mod-php php-mysql
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/install-php.png)

**2. Verify PHP Installation**
- Check the installed PHP version
```
php -v
```
or
```
php --version
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/version.png)

# Create A Virtual Host
In the context of Apache web server, a virtual host refers to the method of hosting multiple websites or web applications on a single server. Each virtual host has its own separate configuration, allowing distinct domain names or IP addresses to be associated with specific directories or settings on the server.

**1. Create Directory for Your Website**
- Create a directory to hold your website's files. For this project, I will be using `myprofile`. Note if you have an existing domain name you can use it for example myprofile.com
```
sudo mkdir /var/www/myprofile
```

**2. Assign Ownership**
- Assign ownership of the directory by using `$USER`
```
sudo chown -R $USER:$USER /var/www/myprofile
```
- Set permissions using the `chmod` command
```
sudo chmod -R 755 /var/www
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/owner.png)


**3. Create a Virtual Host Configuration File**
- Create a blank configuration file using `vi`. Note you can use other editors like `nano` or `vs code`
```
sudo vi /etc/apache2/sites-available/myprofile.conf
```
- while in `vi` take the following steps
* Hit `esc` key and the type `i`. This will take you to the insert mode.
* Copy the code below and paste in your editior
```
<VirtualHost *:80>
   ServerName myprofile
   ServerAlias www.myprofile
   ServerAdmin webmaster@localhost
   DocumentRoot /var/www/myprofile
   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
* Type `:` before typyin `wq` and hitting `ENTER`
* Not sure how exit `vi` watch this [video](https://www.youtube.com/watch?v=KwCvEVblJl8) 
 
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/configuration.png)

- To see the `sites available directory` runn the following command
```
sudo ls /etc/apache2/sites-available
```
You will see something like this `000-default.conf  default-ssl.conf  myprofile.conf`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/sites-available.png)

**4. Enable the Virtual Host**
- Th enable virtual host run the command:
```
sudo a2ensite myprofile
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/enable.png)

**5. Disable Apaches Default Website**
- If you are not using s custom domain, it is adviseable to diable Apache's default website so that Apache's default configuration doesn't overwrite your website.
```
sudo a2dissite 000-default
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/disable.png)

**6. Test Configuration**
- To ensure your configuration doesnt have sytax error, run:
```
sudo apache2ctl configtest
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/config-test.png)

**6. Reload Apache**
- To see your changes. reload Apache
```
sudo systemctl reload apache2
```

**7. Create an HTML File**
- Your website is active but you dont have an `index.html` file to test if the virtual host works. Let's create a none empty file
```
echo "Hello World" > /var/www/myprofile//index.html
```
- However if you want a more informative message that let's your visitors know when your site is down, use:
```
sudo echo 'Hello LAMP from hostname' $(curl -s http://16.16.213.30/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://16.16.213.30/latest/meta-data/public-ipv4) > /var/www/myprofile/index.html
```
Just remeber to change the IP to yours. 

- To see you your `index.html` you use the syntaxt `http://<Public-IP-Address>:80`. If you dont know you IP run the command `curl ifconfig.me`. Oncce you get you public IP copy it and paste in your browser
```
http://16.16.213.30/:80
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/index.png)

# Enable PHP On The Website












  





