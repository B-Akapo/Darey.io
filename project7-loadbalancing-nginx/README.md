# Introduction to Load Balancing with Nginx

Load balancing, a fundamental concept in modern web architectures, involves distributing incoming network traffic across multiple servers to prevent any single server from becoming overloaded. This technique optimizes resource utilization, minimizes response times, and enhances system reliability and scalability.

This project centers on implementing load balancing using Nginx, a versatile web server renowned for its performance and flexibility. Nginx serves as a powerful tool to intelligently distribute incoming requests from clients to multiple servers, ensuring even workload distribution and efficient handling of traffic.

By utilizing Nginx's capabilities for load balancing, this project aims to create a resilient architecture that dynamically allocates incoming requests across server nodes. This README provides comprehensive guidelines for setting up and configuring Nginx to implement effective load balancing, emphasizing the importance of optimal performance, scalability, and seamless client-server interactions in modern web environment

Fantastic now lets get started with our project 

# Getting Started With AWS
If you don't have an AWS account, you'll need to [sign up](https://aws.amazon.com/free/) to access their services. However, if you already have an account, you can skip this step and proceed.

# Setting Up An EC2 Instance
For this project we will be setting up two EC2 Instances. Lets call the first server **"server_one"** and the second one **"server_two"**. If you dont know how to set up and EC2 instance, you can learn [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#setting-up-an-ec2-instance). You can also learn how to connect to your server on your local machine [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#connecting-to-your-ec2-instance-from-your-local-machine)

When you are done, you servers should look like this:

![Alt text](ec2-dashboard.png)

# Open Port 8000
We're planning to have our servers operating on port 8000, with port 80 dedicated to the load balancers. Ensuring unrestricted access, we'll configure the port to allow traffic from all sources. To kick things off, let's start with the setup for `server_one`. 

**Step 1: Go To Security Groups**
- Go back to "instances" on your AWS console.
- Ensure you select `server_one`
- Click on security and then "security group". Please make sure you select the right instance

![Alt text](security_group.png)

**Step 2: Edit Inbound Rules**
- On the security page, scroll on and select **"Edit Inbound Rules"**

![Alt text](edit-inbound.png)

- click on "Add rule" set up the following:

  a. set "Type" to "Custom TCP"

  b. set "Protocol" to "TCP"

  C. set "Port range" to "8000"

  d. set source to "Anywhere IPv4"

  e. Save your details

![Alt text](save-inbound.png)

Now do the same for `server_two`. Remember to select it instead of `server_one`


  




