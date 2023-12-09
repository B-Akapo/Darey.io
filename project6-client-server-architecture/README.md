# Introduction To Client-Server Architecture 
Client-server architecture is a foundational concept in modern computing, defining the relationship and interaction between devices on a network. At its core, this architecture model involves two primary entities: clients, which request services or resources, and servers, which provide these services or resources.

This guide provides a comprehensive overview of client-server architecture, the fundamental framework governing interactions between devices on a network. Exploring the dynamics between clients (requesting resources) and servers (providing services), it demystifies this crucial model for efficient communication, data exchange, and resource sharing across networks.

#
Client-server architecture operates on a fundamental principle: enabling communication and resource sharing between two distinct entities—the client and the server—over a network. Here's a simplified explanation:

- **Clients:** Devices or applications that request services or resources from the server. These could be computers, smartphones, or any device seeking specific data or functionalities.
- **Servers:** Systems or computers that store data, applications, or resources and fulfill client requests. Servers are designed to provide these services upon receiving valid requests from clients.

# How It Works
- **Request-Response Model**: Clients send requests to servers, specifying the service or data they require.
- **Server Processing:** Upon receiving a request, the server processes it, retrieves the requested information, performs necessary computations, or executes tasks.
- **Response Transmission:** The server sends back the requested data or performs the requested action.
- **Client-Side Handling:** Clients receive the response and utilize the provided data or services as needed.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/archi1.png)

It is interesting to note, that in the client-server architecture you can also add a Database Server. Let quickly look at a diagram

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/archi2.png)

In the diagram above, 

- **The client sends a GET request to the web server:**  The GET request is used to retrieve data from a web server. The request includes the URL of the resource being requested, as well as any query parameters.
- **The web server receives the GET request and connects to the MySQL database:** The web server receives the GET request from the client and connects to the MySQL database. The web server then executes the query specified in the request.
- **The web server sends the results of the query back to the client:** The web server sends the results of the query back to the client.

# Key Components Of A Client-Server Architecture:
- **Communication Protocols:** Define the rules for data exchange between clients and servers (e.g., HTTP, TCP/IP).
- **Client-Side Applications:** Software or interfaces that enable users to interact with the server (e.g., web browsers, apps).
- **Server-Side Applications:** Programs or systems responsible for processing requests and providing services or data to clients (e.g., web servers, databases).

Now that we kind of understand how the client-server architecture works, let us practice it. 

# Getting Started With AWS
If you don't have an AWS account, you'll need to [sign up](https://aws.amazon.com/free/) to access their services. However, if you already have an account, you can skip this step and proceed.

# Setting Up An EC2 Instance
For this project we will be setting up two EC2 Instances. Lets call the first server **"mysql_server"** and the second one **"mysql_client"**. If you dont know how to set up and EC2 instance, you can learn [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#setting-up-an-ec2-instance). You can also learn how to connect to your server on your local machine [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#connecting-to-your-ec2-instance-from-your-local-machine)

When you are done, you servers should look like this:

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/ec2.png)

# Installing MySQL Server Software
On the `mysql_server`, we are going to install MySQL Server Software. MySQL is a Relational Database Management System (RDBMS) that allows you to store and manage data for your server/site. If you dont know how to install MySQL, you can find a detailed step-by-step guide [here](https://github.com/B-Akapo/Darey.io/tree/main/project3-deploying_A_LAMP_Application#installing-mysql)

# Create New User and Give privileges
Now lets create a new user and grant privileges. It is with this user credentials you will access `mysql-server` from `mysql_client`. You can learn how to do this [here](https://github.com/B-Akapo/Darey.io/tree/main/project4-deploying-LEMP-Application#retrieving-data-from-mysql-database-using-php)

# Installing MySQL Client Software
On the `mysql_client` we are going to instal the MySQL Client Software and not the Server SOftware because We want to be able to connect to the MySQL server on our mysql_server instance, from the mysql_client instance. Installing the client server is easy.

**Step 1: Update Packages**
```
sudo apt update
```
**Step 2: Upgrade Packages**
```
sudo apt upgrade
```
**Step 3: Install Client Software**
```
sudo apt install mysql-client
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/client-server.png)

# Open TCP Port 3306
Your two EC2 servers talk to each other using local IP addresses. To connect from mysql_client to mysql_server, use mysql_server's local IP address. For this to work, open TCP port 3306 in 'mysql_server' Security Groups. To enhance security, limit access to 'mysql_server' by specifying only the local IP address of 'mysql_client'.

**Step 1: Go To Security Groups**
- Go back to "instances" on your AWS console.
- Ensure you select `mysql_server`
- Click on security and then "security group". Please make sure you select the right instance

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/security-group.png)

- In the "Security" page click on "Edit inbound rules"

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/inbound-rules.png)

- click on "Add rule" set up the following:

  a. set "Type" to "MYSQL/Aurora"

  b. set "Protocol" to "TCP"

  C. set "Port range" to "3306"

  d. set source to <the private IP address of `mysql_client`>/32. You can find this on the instance dashboard

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/private-ip.png)

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/new-inbound.png)

  e. save rules

# Configure MySQL Server
You should et up mysql_server to permit connections from other devices or hosts. 
- To do this run the following comand on the terminal of your `mysql_server`. 
```
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
```
You can use the editor of your choice. I am using `vi`. 
- Replace ‘127.0.0.1’ to ‘0.0.0.0’. To do this in `vi`, Hit `Esc key` and the type `i`. This will take you to the insert mode where you can edit.

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/no-change.png)

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/change.png)

- When done editing, Hit `Esc` again then Type `:wq` and hitting `ENTER`. Not sure how exit vi watch this [video](https://www.youtube.com/watch?v=KwCvEVblJl8)

# Connect The Client Server. 
Alright. our servers are up, our permissions set, lets now conntect to `mysql_server` without using ssh. It is simple to do. 
- First lets ping our server to see if we can connect
```
ping 172.31.29.148
```
Note: Replace the IP address with your own `mysql_server` IP. which you can find on you AWS console or by running the command `hostname -I`

- You should see that you client server can connect to your server. If you get an error try checking your IP address. or running an error log on your `mysql_server` to see what is going on. Use the command `sudo tail -f /var/log/auth.log`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/ping.png)

- On `mysql_client`, run the following command
```
mysql -u devops -h 172.31.29.148 -p
```
or
```
mysql -u devops -h 172.31.29.148 -p name_database
```
NOTE: The IP address is the private IP of your `mysql_server` 

- You shoud be able to connect to you server database. To test, on the MySQL console run the command
```
SHOW DATABASES;
```
- And you should see your database right there. in my own case it is called `name_database`

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project6-client-server-architecture/images/client-access.png)

- To see your tables, you canrun the following command on your MySQL console
```
SHOW TABLES;
```
Well done, you can now connect form your client server to your server database. 
















