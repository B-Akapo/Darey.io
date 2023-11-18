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

![Alt text](pem-file)

3. Set Permissions for the PEM Key
- Set appropriate permissions to the key file. The syntaxt is
 ```
 chmod 400 <your-key>.pem
 ```
![Alt text](pem-permission)  

Dont worry if you don't see anything on the screen. It means it worked. `chmod 400` sets the permissions so that only the owner of the file has read access, while all other users (group and others) have no permissions to read, write, or execute the file. To see if your permission is set run the comman `ls -al` on your terminal 

![Alt text](check-pem-permission) 

**4. Connect To EC2 Using SSH**
- In the terminal, use SSH to connect to your EC2 instance using the syntax
```
ssh -i /path/to/your-key.pem ec2-user@your-ec2-public-ip
```
Dont worry if you dont remeber it. It is easy to get.
   * First got to your AWS console and go to `instances`
   * MAke sure the instance you want is selected and the click on `connect`
     
![Alt text](instance-check) 

   * While in connection dashboard, go to `SSH Client`, copy the whole code under "Example" and paste in your terminal and hit enter.
     
![Alt text](client-ssh) 

And that's it, you are now connected to your EC2 instance on your local machine. 

![Alt text](connected) 



