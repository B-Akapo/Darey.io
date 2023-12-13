# Table Of Content
# Table of Contents

1. [**Introduction to Load Balancing with Nginx**](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#introduction-to-load-balancing-with-nginx)
2. [**Getting Started**](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#getting-started-with-aws)
3. [**Setting Up An EC2 Instance**](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#setting-up-an-ec2-instance)
    - [Open Port 8000](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#open-port-8000)
    - [Connecting To Your EC2 Instance From Your Local Machine](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#connecting-to-your-ec2-instance-from-your-local-machine)
4. [**Installing Apache Webserver**](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#installing-apache-webserver)
5. [**Provisioning Nginx Server**](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#provisioning-nginx-server)
    - [Opening Port 80](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#open-port-80)
    - [Installing Nginx](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#installing-nginx)
6. [**Configuring Nginx as a Load Balancer**](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#configuring-nginx-to-act-as-a-loadbalancer)
    - [Testing Nginx Load Balancer Setup](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#restart-nginx)
#
# Introduction to Load Balancing with Nginx

Load balancing, a fundamental concept in modern web architectures, involves distributing incoming network traffic across multiple servers to prevent any single server from becoming overloaded. This technique optimizes resource utilization, minimizes response times, and enhances system reliability and scalability.

This project centers on implementing load balancing using Nginx, a versatile web server renowned for its performance and flexibility. Nginx serves as a powerful tool to intelligently distribute incoming requests from clients to multiple servers, ensuring even workload distribution and efficient handling of traffic.

By utilizing Nginx's capabilities for load balancing, this project aims to create a resilient architecture that dynamically allocates incoming requests across server nodes. This README provides comprehensive guidelines for setting up and configuring Nginx to implement effective load balancing, emphasizing the importance of optimal performance, scalability, and seamless client-server interactions in modern web environment

Fantastic now lets get started with our project 

# Getting Started With AWS
If you don't have an AWS account, you'll need to [sign up](https://aws.amazon.com/free/) to access their services. However, if you already have an account, you can skip this step and proceed.

# Setting Up An EC2 Instance
For this project we will be setting up two EC2 Instances. Lets call the first server **"server_one"** and the second one **"server_two"**. If you dont know how to set up and EC2 instance, you can learn [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#setting-up-an-ec2-instance).

When you are done, you servers should look like this:

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/ec2-dashboard.png)

# Open Port 8000
We're planning to have our servers operating on port 8000, with port 80 dedicated to the load balancers. Ensuring unrestricted access, we'll configure the port to allow traffic from all sources. To kick things off, let's start with the setup for `server_one`. 

**Step 1: Go To Security Groups**
- Go back to "instances" on your AWS console.
- Ensure you select `server_one`
- Click on security and then "security group". Please make sure you select the right instance

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/security_group.png)

**Step 2: Edit Inbound Rules**
- On the security page, scroll on and select **"Edit Inbound Rules"**

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/edit-inbound.png)

- click on "Add rule" set up the following:

  a. set "Type" to "Custom TCP"

  b. set "Protocol" to "TCP"

  C. set "Port range" to "8000"

  d. set source to "Anywhere IPv4"

  e. Save your details

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/save-inbound.png)

Now do the same for `server_two`. Remember to select it instead of `server_one`

# Connecting To Your EC2 Instance From Your Local Machine
Connecting to your EC2 from you local machine is easy. I have a detailed guide you can find [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#connecting-to-your-ec2-instance-from-your-local-machine). 

# Installing Apache Webserver
Now that we have our servers running both on the cloud and our local machine, let is install Apache on both servers. 

**Step 1: Update and Upgrade Package Lists**
- Update the package lists to ensure you have the latest information about available packages
```
sudo apt update && sudo apt upgrade -y
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/upgrade.png) 

**Step 2: Install Apache**
- Install the Apache package using `apt`
```
sudo apt install apache2
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/install-apache.png) 

**Step 3: Check Apache Service Status**
- To confirm that Apache is running as a service
```
sudo systemctl status apache2
```
Once you see green and active, you are good to go. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/apache-status.png) 

**Step 4: Configure Apache to Serve Content On Port 8000**
Let's adjust our webserver settings to deliver content on port 8000 instead of the default port 80. To do this you will need a code editor, I will be using `vim`. 
```
sudo vi /etc/apache2/ports.conf 
```
- Add a new listening directive for port 8000. Basically change `Listen 80` to `Listen 8000`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/no-change.png)

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/change.png)

- Change port on the virtual host from 80 to 8000
```
sudo vi /etc/apache2/sites-available/000-default.conf
````

![Alt tetx](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/virtual-host-nochange.png)

![Alt tetx](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/virtual-host-change.png)

- Now save your file using `:wqa!`
- Restart Apache
```
sudo systemctl restart apache2
```

**Step 4: Create index.html file**
- Create a new index.html file by running this code
```
sudo vi index.html
```
- Copy and paste to code below into your file
```
<!DOCTYPE html>
<html>
<head>
        <title>My EC2 Instance</title>
</head>
<body>
        <h1>Welcome to my EC2 instance</h1>
        <p>Public IP: YOUR_PUBLIC_IP</p>
</body>
</html>
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/index-file.png)

**Step 5: Configure ownership of index.html file**
- lets ensure that we have the right permission
```
sudo chown www-data:www-data ./index.html
```

**Step 6: Override the default html of Apache Webserver**
- Let's replace the default html file with our `index.html`
```
sudo cp -f ./index.html /var/www/html/index.html
```
- Restart Apache
```
sudo systemctl restart apache2
```
**Step 7: Check Port In Local Machine**
- To ensure you have access to the port, run the following command
```
curl http://localhost:8000
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/local-machine.png)

If you see the screen above it means you can access the local port. That is awesome

**Step 8: Apache Server On Browser**
- Now instead of using the HTML file. Let's access the file on our browser. First get your EC2 public IP
```
curl ifconfig.me
```
![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/curl.png)

- Or you can just go to your AWS console and scroll to the right and find your public IP address

![Alt text](https://github.com/B-Akapo/Darey.io/raw/main/project3-deploying_A_LAMP_Application/images/address2.png)

- Once you have your IP you can just copy it into the browser or use **http://<Public-IP-Address>:80** and you should be able to access the site. In my own case it is:
```
http://16.16.57.37:8000
```
You should see our index.html file. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/apache1.png)

**Now do steps 1 - 8 for** `server_two`

# Provisioning Nginx Server
- Next we a going to provision and EC2 instance for the Nginx server to act as the loadbalancer. Lets call it `nginx_server`. To do this, simply follow the same guide [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#setting-up-an-ec2-instance).

# Open Port 80
Jus like before we will open a port but this time it is port 80 and NOT 8000. Follow the same steps [here](https://github.com/B-Akapo/Darey.io/tree/main/project7-loadbalancing-nginx#open-port-8000)

# Installing Nginx
**Step 1: Update and Upgrade Package Lists**
- Update the package lists to ensure you have the latest information about available packages
```
sudo apt update && sudo apt upgrade -y
```

**Step 2: Install Nginx**
- Install the Nginx package using `apt`
```
sudo apt install nginx
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/install-nginx.png)

**Step 3: Check Nginx Service Status**
- To confirm that Apache is running as a service
```
sudo systemctl status nginx
```
Once you see green and active, you are good to go. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/nginx-status.png)

# Configuring Nginx To Act As A Loadbalancer
- Open Nginx configuration file
```
sudo vi /etc/nginx/conf.d/loadbalancer.conf
```
- Copy and paste the code below into your editor. Remember to change the IP adress to your server IPs (like I did in the image below). You can use `curl ifconfig.me` to get your IP addresses.
```
upstream backend_servers {

        # your are to replace the public IP and Port to that of your webservers
        server 127.0.0.1:8000; # public IP and port for webserser 1
        server 127.0.0.1:8000; # public IP and port for webserver 2
}

server {

        listen 80;
        server_name <your load balancer's public IP addres>; # provide your load balancers public IP address

        location / {

                proxy_pass http://backend_servers;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
}
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/loadbalance-config.png)
    
- Save your file and exit

# Restart Nginx
- First make sure your config file is error proof run the command
```
sudo nginx -t
```
Generally it should be okay. But if it isn't check the error message to see the line of code that has an issue

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/test-config.png)

- If there is no error, you need to restart your nginx service.
```
sudo systemctl restart nginx
```

# Nginx On Browser
- now copy your your Nginx server IP on your browser. Remember it is on Port 80
```
http://16.16.186.103:80
```
What should happen is that you should see your loadbalancer switching between your servers. If you check the screen you should see both IP addresses changing. If you are not seeing it, do a hard reset `SHIFT + Left click mouse`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/loadbalancer1.png)

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/loadbalancer2.png)

Nginx operates as a load balancer by distributing incoming web traffic across multiple servers. The screenshots display the IP addresses of `server_one` and `server_two`. When you repeatedly refresh or reload the page, Nginx dynamically switches the requests between these servers. This seamless switching demonstrates how Nginx effectively balances the load by evenly distributing incoming requests among the available servers. Essentially, it acts as a traffic manager, optimizing performance and ensuring efficient resource utilization across the server pool.




















  




