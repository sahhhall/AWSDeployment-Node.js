
# Steps to Deploy a Node.js Application


## AWS (Amazon Web Services)
AWS is a cloud computing platform provided by Amazon.
![AWS](/images/aws.webp)
It consists of various remote computing services like Amazon EC2 instances, various types of databases, and networking options.

## AWS EC2 (Elastic Compute Cloud)
Amazon EC2 is Amazon Elastic Cloud Computing. This is a service where Amazon provides us a server where we can deploy our application for an absolute minimum cost, and it takes very little time to do so.
![EC2](/images/ec2.webp)
By providing the service of AWS EC2, Amazon is giving us an easy way to launch our application without worrying about the bare metal hardware stuff and the networking part.

## Linux AMI
An Amazon Machine Image (AMI) is a pre-configured virtual machine image, available in the Amazon Web Services (AWS) ecosystem, that is used to launch an instance.
![Linux AMI](/images//AMI.webp)
A Linux AMI comes pre-installed with a Linux operating system. Some of the most popular Linux distributions available as AMIs on AWS are Ubuntu and Amazon Linux.


## Table of Contents
* [General Info](#general-info)
* [AWS setup](#create-an-aws-account)
* [Initial Server Setup for Ubuntu](#initial-server-setup-for-ubuntu)
* [Setting Up a Domain Name](#setting-up-a-domain-name)
* [Enabling Security](#enabling-security)
* [Installing Nginx](#installing-nginx)
* [Securing Nginx with Let's Encrypt](#securing-nginx-with-lets-encrypt)
* [Installing Node.js](#installing-nodejs)
* [Nginx Commands](#nginx-commands)
* [PM2 Commands](#pm2-commands)
* [Linux Commands](#linux-commands)

## General Info
This guide provides a comprehensive overview of setting up a Node.js application on AWS EC2, including the necessary configurations and security measures.


## Create an AWS Account
1. **Visit the AWS Website**: Navigate to the AWS homepage and locate the "Create an AWS Account" option.
2. **Begin Account Creation**: Click on "Create an AWS Account" and follow the prompts to initiate the registration process.
3. **Enter Account Information**: Provide your email address, a secure password, and other necessary details as prompted.
4. **Payment Information**: Input your credit card details for billing purposes. Note that some services may offer a free tier for new users.

   
### **Take EC2 Dashboard**

**Access AWS Management Console**: Log in to the AWS Management Console using your newly created account credentials.

**Navigate to EC2 Dashboard**: From the console dashboard, locate and select the EC2 service to enter the EC2 Dashboard.

   
### **Launch an EC2 Instance**

**Initiate Instance Creation**: Within the EC2 Dashboard, click on "Launch Instance" to commence the creation of a new EC2 instance.

**Understanding EC2**: EC2, or Elastic Compute Cloud, provides scalable computing capacity in the AWS cloud, enabling organizations to develop and deploy applications without upfront commitments. It automates hardware and connectivity requirements, streamlining the deployment process.

   
### **Choose an Amazon Machine Image (AMI)**

**Select Suitable AMI**: Choose an appropriate Amazon Machine Image (AMI) that aligns with your application requirements. Common choices include Amazon Linux, Ubuntu, and Windows Server.

   
### **Select an Instance Type**

**Choose Hardware Configuration**: Select an instance type that suits your needs in terms of CPU, memory, storage, and networking capacity. For beginners, t2.micro, eligible for the free tier, is often recommended.

   
### **Configure Instance Details**

**Specify Configuration Settings**: Configure instance details such as the number of instances, network settings, and other parameters. Default settings are generally adequate for beginners.

   
### **Add Storage**

**Define Storage Requirements**: Determine the size and type of storage needed for your instance. Default storage settings can typically be retained, although customization options are available based on specific needs.

   
### **Add Tags**

**Organize Resources with Tags**: Optionally, add tags to your instance using key-value pairs to facilitate management and organization of AWS resources.

   
### **Configure Security Group**

**Set Up Security Measures**: Configure a security group to regulate traffic to your instance, ensuring network security. Default settings usually include allowing SSH (port 22) for Linux instances or RDP (port 3389) for Windows instances.

   
### **Review and Launch**

**Confirm Instance Settings**: Review all configured settings for your instance and proceed to launch it.

**Key Pair Selection**: Choose or create a key pair for secure instance access. Download the key pair file (.pem) and securely store it for future use.

   
### **Access Your Instance**

**Establish Connection**: Access your instance using the provided SSH command found in the instance details. 

**Terminal Access**: Open a terminal window, navigate to the directory where your key pair file is stored, and connect to your instance using the SSH command.

   
## Follow This Tutorial

**Follow the steps in this tutorial to set up a Node.js application for production on Ubuntu 22.04:**

[How To Set Up a Node.js Application for Production on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu)

### 1. Initial Server Setup for Ubuntu
Complete the steps in the "Initial Server Setup with Ubuntu 22.04" section, which includes updating the server, creating a new user (optional), and setting up a basic firewall.

### 2. Setting Up a Domain Name
To set up a domain name:
- Purchase a domain name from a registrar like GoDaddy or Hostinger.

- In AWS, use **Route 53** to manage your domain:
  - Create a hosted zone: Enter your domain name and create the hosted zone. This will provide you with four name server (NS) records.
  - In your domain registrar (e.g., Hostinger), update the DNS settings to use the four NS records provided by Route 53.

### 3. Enabling Security
- In the EC2 dashboard, go to the **Security Groups** associated with your instance.
- Edit the **Inbound Rules** to allow HTTP (port 80) and HTTPS (port 443) traffic.

### 4. Installing Nginx
Nginx is a powerful web server software that can also be used as a reverse proxy, load balancer, and HTTP cache.

Follow this guide to install Nginx on your Ubuntu server:
[How To Install Nginx on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04)

### 5. Securing Nginx with Let's Encrypt
Use Let's Encrypt to obtain a free SSL certificate and secure your Nginx server.

```bash
sudo snap install --classic certbot

sudo ln -s /snap/bin/certbot /usr/bin/certbot

sudo certbot --nginx -d example.com -d www.example.com

```

Follow this guide:
[How To Secure Nginx with Let's Encrypt on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04)


Follow these steps to install Node.js, clone your project repository, install dependencies, and set up MongoDB:

Install Node.js:
[Follow this guide to install Node.js on your Ubuntu server](https://www.freecodecamp.org/news/how-to-install-node-js-on-ubuntu/#:~:text=After%20installing%20Node%20and%20NPM,Hello%20World%22%20type%20Node%20project.&text=Now%20run%20the%20setup%20with,a%20new%20file%20called%20app)

Clone Your Project Repository:
git clone `https://github.com/your-username/your-repo.git`
`cd your-repo`

Install NPM Dependencies:
Start Your Node.js Application:

To use PM2 to manage your Node.js application and ensure it continues running even after closing the terminal :)

### NGINX COMMANDS
```
Stop: sudo systemctl stop nginx
Start: sudo systemctl start nginx
Restart: sudo systemctl restart nginx
Reload: sudo systemctl reload nginx
Disable: sudo systemctl disable nginx
Enable: sudo systemctl enable nginx
Check status: sudo systemctl status nginx
```

### PM2 COMMANDS
```
pm2 start: Start process
pm2 list: List processes
pm2 stop: Stop process
pm2 restart: Restart process
pm2 reload: Reload process
pm2 delete: Delete process
pm2 logs: Show process logs
pm2 monit: Monitor processes
pm2 save: Save processes
pm2 startup: Configure startup
```

### LINUX COMMANDS
```
sudo: Super user do
ls: List files
pwd: Print directory that currently working
cd: Change directory
mkdir: Make directory
mv: Move file
cp: Copy file
rm: Remove file
cat: create a file , display, copy content of one file to another file
touch: Create file
clear: Clear terminal
wget: Download file
echo: allows users to display text or variables in a variety of ways
sudo apt-get update: Update packages 
sudo apt-get upgrade: Upgrade packages
chmod: Change file mode
chown: Change file owner
```

Feel free to provide the next step or any additional instructions!