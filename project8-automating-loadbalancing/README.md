# Table of Contents
1. [Introduction](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#introduction)
2. [Getting Started With AWS](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#getting-started-with-aws)
3. [Setting Up An EC2 Instance](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#setting-up-an-ec2-instance)
   - [Open Port 8000](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#open-port-8000)
   - [Connecting To Your EC2 Instance From Your Local Machine](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#connecting-to-your-ec2-instance-from-your-local-machine)
4. [Creating The Apache Automation Script](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#creating-the-apache-automation-script)
5. [Provisioning Nginx Server](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#provisioning-nginx-server)
   - [Open Port 80](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#open-port-80)
6. [Creating The Nginx Loadbalancing Automation Script](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/README.md#creating-the-nginx-loadbalancing-automation-script)

#

# Introduction
Load balancing is a critical aspect of managing modern computing environments, ensuring efficient distribution of incoming network traffic across multiple servers or resources. It plays a pivotal role in optimizing performance, reliability, and scalability of systems by preventing any single server from being overwhelmed, thus enhancing overall user experience.

For DevOps Engineers, automating the load balancing process is a fundamental practice. Automation streamlines the setup, configuration, and maintenance of load balancers, reducing manual intervention and enabling swift, consistent deployments. This approach allows for dynamic adjustments in response to changing demands, ensuring systems can adapt effectively to varying traffic patterns and server loads. Automating load balancing is key to achieving resilience, scalability, and agility in complex and dynamic environments, making it an indispensable element of modern DevOps practices.

In this project, I've explored the automation of load balancing using shell scripting, aiming to simplify and expedite the configuration process while emphasizing the significance of this automation for DevOps Engineers.

We are going to repeat the first few processes from Project 7. You can refer to it [here](https://github.com/B-Akapo/Darey.io/tree/main/project7-loadbalancing-nginx)

# Getting Started With AWS
If you don't have an AWS account, you'll need to [sign up](https://aws.amazon.com/free/) to access their services. However, if you already have an account, you can skip this step and proceed.

# Setting Up An EC2 Instance
For this project we will be setting up two EC2 Instances. Lets call the first server **"server_one"** and the second one **"server_two"**. If you dont know how to set up and EC2 instance, you can learn [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#setting-up-an-ec2-instance).

When you are done, you servers should look like this:

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/images/ec2-dashboard.png)

# Open Port 8000
Opening your port is not hard. [Here](https://github.com/B-Akapo/Darey.io/blob/main/project7-loadbalancing-nginx/README.md#open-port-8000) is a step-by-step guide to help. 

# Connecting To Your EC2 Instance From Your Local Machine
Connecting to your EC2 from you local machine is easy. I have a detailed guide you can find [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#connecting-to-your-ec2-instance-from-your-local-machine).

# Creating The Apache Automation Script
Now that we have our servers, lets write our scripts. We will start with `server_one`. New to shell scripting, that's fine, learn about shell scripting, you can explore [this](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting) documentation. 

**Step 1: New Script File**
- Create a new script file. I am calling mine `install.sh`. You can name yours whatever you want
```
sudo vi install.sh
```
- copy the code below and paste in your editor. remember to edit to fit you IP addresses. Just like I have pointed in the image below. To get you IP run the command `curl ifconfig.me`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/images/scritpt-server1.png)

```
#!/bin/bash

####################################################################################################################
##### This automates the installation and configuring of apache webserver to listen on port 8000
##### Usage: Call the script and pass in the Public_IP of your EC2 instance as the first argument as shown below:
######## ./install_configure_apache.sh 127.0.0.1
####################################################################################################################

set -x # debug mode
set -e # exit the script if there is an error
set -o pipefail # exit the script when there is a pipe failure

PUBLIC_IP=$1

[ -z "${PUBLIC_IP}" ] && echo "Please pass the public IP of your EC2 instance as an argument to the script" && exit 1

sudo apt update -y &&  sudo apt install apache2 -y

sudo systemctl status apache2

if [[ $? -eq 0 ]]; then
    sudo chmod 777 /etc/apache2/ports.conf
    echo "Listen 8000" >> /etc/apache2/ports.conf
    sudo chmod 777 -R /etc/apache2/

    sudo sed -i 's/<VirtualHost \*:80>/<VirtualHost *:8000>/' /etc/apache2/sites-available/000-default.conf

fi
sudo chmod 777 -R /var/www/
echo "<!DOCTYPE html>
        <html>
        <head>
            <title>My EC2 Instance</title>
        </head>
        <body>
            <h1>Welcome to my EC2 instance</h1>
            <p>Public IP: "${PUBLIC_IP}"</p>
        </body>
        </html>" > /var/www/html/index.html

sudo systemctl restart apache2
```
- Save you file and exit your editor using `SHIFT + :wqa!`

**Step 2: Set File Permission**
- Change the permission of you script file.
```
sudo chmod +x install.sh
```
**Step 3: Run Script**
- Run you script using the command.
```
./install.sh PUBLIC_IP
```
If all goes well, you should have something like the screen below

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/images/run-apache-script.png)

Great!!! Now do the exact same thing for `server_two`

**Step 4: Apache Server On Browser**
- Let's access the file on our browser. First get your EC2 public IP `curl ifconfig.me`
- Once you have your IP you can just copy it into the browser or use http://:8000 and you should be able to access the site. In my own case it is:
```
http://51.20.98.67:8000/
```

# Provisioning Nginx Server
Now lets provision the EC2 instance for our Nginx server. Let's call in `nginx_server`. The [same guide](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#setting-up-an-ec2-instance) still applies.

# Open Port 80
Just like before we will open a port but this time it is port 80 and NOT 8000. Follow the same steps [here](https://github.com/B-Akapo/Darey.io/tree/main/project7-loadbalancing-nginx#open-port-8000)

# Creating The Nginx Loadbalancing Automation Script
Now that we have our server, lets write our script. 

**Step 1: New Script File**
- Create a new script file. I am calling mine `nginx.sh`. You can name yours whatever you want
```
sudo vi nginx.sh
```
- copy the code below and paste in your editor. remember to edit to fit you IP addresses. Just like I have pointed in the image below. To get you IP run the command `curl ifconfig.me`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/images/nginx-script.png)

```
#!/bin/bash

######################################################################################################################
##### This automates the configuration of Nginx to act as a load balancer
##### Usage: The script is called with 3 command line arguments. The public IP of the EC2 instance where Nginx is installed
##### the webserver urls for which the load balancer distributes traffic. An example of how to call the script is shown below:
##### ./configure_nginx_loadbalancer.sh PUBLIC_IP Webserver-1 Webserver-2
#####  ./configure_nginx_loadbalancer.sh 127.0.0.1 192.2.4.6:8000  192.32.5.8:8000
############################################################################################################# 

PUBLIC_IP=$1
firstWebserver=$2
secondWebserver=$3

[ -z "${PUBLIC_IP}" ] && echo "Please pass the Public IP of your EC2 instance as the argument to the script" && exit 1

[ -z "${firstWebserver}" ] && echo "Please pass the Public IP together with its port number in this format: 127.0.0.1:8000 as the second argument to the script" && exit 1

[ -z "${secondWebserver}" ] && echo "Please pass the Public IP together with its port number in this format: 127.0.0.1:8000 as the third argument to the script" && exit 1

set -x # debug mode
set -e # exit the script if there is an error
set -o pipefail # exit the script when there is a pipe failure


sudo apt update -y && sudo apt install nginx -y
sudo systemctl status nginx

if [[ $? -eq 0 ]]; then
    sudo touch /etc/nginx/conf.d/loadbalancer.conf

    sudo chmod 777 /etc/nginx/conf.d/loadbalancer.conf
    sudo chmod 777 -R /etc/nginx/

    
    echo " upstream backend_servers {

            # your are to replace the public IP and Port to that of your webservers
            server  "${firstWebserver}"; # public IP and port for webserser 1
            server "${secondWebserver}"; # public IP and port for webserver 2

            }

           server {
            listen 80;
            server_name "${PUBLIC_IP}";

            location / {
                proxy_pass http://backend_servers;   
            }
    } " > /etc/nginx/conf.d/loadbalancer.conf
fi

sudo nginx -t

sudo systemctl restart nginx
```

- Save you file and exit your editor using `SHIFT + :wqa!`

**Step 2: Set File Permission**
- Change the permission of you script file.
```
sudo chmod +x nginx.sh
```
**Step 3: Run Script**
- Run you script using the command.
```
./nginx.sh PUBLIC_IP Webserver-1 Webserver-2
```
If all goes well, you should have something like the screen below

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/images/nginx.png)

**Step 4: Nginx On Browser**
- now copy your your Nginx server IP on your browser. Remember it is on Port 80
```
http://13.53.176.62:80
```
- What should happen is that you should see your loadbalancer switching between your servers. If you check the screen you should see both IP addresses changing. If you are not seeing it, do a hard reset `SHIFT + Left click mouse`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/images/1.png)

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project8-automating-loadbalancing/images/2.png)

Fantastic, now we have automated our loadbalancing. 











