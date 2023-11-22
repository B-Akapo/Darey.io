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
- Open TCP Port 80: Port 80 is the default port for most web broswers. Lets quickly see how to open it. 
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
curl http://localhost:80
```
or 
```
curl http://127.0.0.1:80
```
The two commands will give the same output which is the raw HTML code of the website. THe first command uses the `DNS name`. The second comand uses the `IP Address`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project3-deploying_A_LAMP_Application/images/port-80.png)

# Installing Nginx
