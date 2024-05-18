---

#### **Create an AWS Account**

1. **Visit the AWS Website** and click on "Create an AWS Account."
2. **Follow the Prompts** to enter your email address, password, and account information.
3. **Provide Payment Information** (credit card details) for billing purposes. Some services may offer a free tier for new users.

#### **Take EC2 Dashboard**

1. **Log into the AWS Management Console**.
2. **Navigate to the EC2 Dashboard**. This is where you'll manage your EC2 instances.

#### **Launch an EC2 Instance**

1. In the **EC2 Dashboard**, click on "Launch Instance" to create a new EC2 instance.
2. **What is EC2?**  
   EC2 (Elastic Compute Cloud) provides scalable computing capacity in the AWS cloud. It enables organizations to develop and deploy applications without the need for upfront commitments. Unlike on-premises infrastructure, where you need to invest funds before creating app serer, EC2 instances handle all the hardware and connectivity requirements automatically.

#### **Choose an Amazon Machine Image (AMI)**

1. **Select an AMI**: Choose an Amazon Machine Image that suits your requirements. AMIs include the OS and applications for your instance. Common choices are Amazon Linux, Ubuntu, and Windows Server.

#### **Select an Instance Type**

1. **Choose an Instance Type**: Select the hardware configuration of your instance. Instance types vary by CPU, memory, storage, and networking capacity. For general purposes, t2.micro (which is eligible for the free tier) is a good starting point.

#### **Configure Instance Details**

1. **Configure Instance Details**: Specify the number of instances, network settings, and other configurations. The default settings are often sufficient for beginners.

#### **Add Storage**

1. **Add Storage**: Define the size and type of storage for your instance. The default storage size and type can usually be left as is, but you can customize it based on your needs.

#### **Add Tags**

1. **Add Tags**: Optionally, you can add tags to your instance. Tags are key-value pairs that help you manage and organize your AWS resources.

#### **Configure Security Group**

1. **Configure Security Group**: Set up a security group to control the traffic to your instance. By default, allow SSH (port 22) for Linux instances or RDP (port 3389) for Windows instances.

#### **Review and Launch**

1. **Review and Launch**: Review your instance settings, and click on "Launch."
2. **Select or Create a Key Pair**: Choose an existing key pair or create a new one to securely connect to your instance. Download the key pair file (.pem) and store it securely (don't remove that key; we need it after a few steps).

#### **Access Your Instance**

1. **Connect Step**: In the SSH tab of your instance details, you will find an example command to connect to your instance. Copy that command.
2. **Take Terminal**: Open a terminal window, navigate to the directory where your .pem file is stored, and paste the copied SSH command to connect to your instance.

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

Follow this guide:
[How To Secure Nginx with Let's Encrypt on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04)

### 6. Installing Node.js
Follow these steps to install Node.js, clone your project repository, install dependencies, and set up MongoDB:

Install Node.js:
Follow this guide to install Node.js on your Ubuntu server:
How to Install Node.js on Ubuntu

Clone Your Project Repository:
git clone https://github.com/your-username/your-repo.git
cd your-repo

Install NPM Dependencies:
Start Your Node.js Application:

To use PM2 to manage your Node.js application and ensure it continues running even after closing the terminal :)

Feel free to provide the next step or any additional instructions!