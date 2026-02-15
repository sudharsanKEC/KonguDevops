
day_aws_devops_ec2_linux_setup: |
  # AWS DevOps EC2 Linux Setup and Global HTML Hosting

  This document records my complete beginner DevOps hands-on journey using AWS. It covers launching an Ubuntu EC2 instance, connecting via SSH from Windows, configuring IAM admin access, installing AWS CLI, preparing Terraform environment, and hosting a globally accessible HTML webpage.

  ---

  ## 📘 Introduction

  AWS provides cloud-based virtual servers using EC2. In this session, an Ubuntu Linux server was created and accessed remotely. Basic DevOps foundations such as SSH access, IAM permissions, AWS CLI authentication, and web hosting were practiced.

  This setup forms the base for further DevOps tools like Docker, Jenkins, and Terraform.

  ---

  ## ⚙️ Environment Used

  - Windows system (PowerShell)
  - AWS EC2 Ubuntu Server 22.04
  - IAM Admin User
  - AWS CLI
  - Apache Web Server

  ---

  ## 🚀 EC2 Ubuntu Instance Creation

  Steps followed:

  - Logged into AWS Console
  - Navigated to EC2
  - Launched new instance
  - Selected Ubuntu Server 22.04 LTS
  - Chose instance type t2.micro / t3.micro
  - Created key pair: devops-key.pem
  - Enabled SSH access from Anywhere IPv4 (0.0.0.0/0)
  - Launched instance
  - Copied Public IPv4 address

  Instance entered Running state successfully.

  ---

  ## 🔑 Connecting to Linux from Windows

  Opened PowerShell and navigated to Downloads:

  cd Downloads

  Connected using SSH:

  ssh -i devops-key.pem ubuntu@PUBLIC_IP

  Successful login displayed:

  ubuntu@ip-xxx:~$

  This confirmed remote Linux access.

  ---

  ## 🛠 Basic Linux Preparation

  Updated server packages:

  sudo apt update  
  sudo apt upgrade -y

  ---

  ## 🔐 IAM Admin User Setup

  Created IAM user named terraform-admin.

  Attached policy:

  AdministratorAccess

  Generated Access Keys (CLI):

  - Access Key ID
  - Secret Access Key

  These credentials allow programmatic access for AWS CLI and Terraform.

  ---

  ## 📦 AWS CLI v2 Installation

  Ubuntu 22.04 does not include awscli by default, so AWS CLI v2 was installed manually.

  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o awscliv2.zip  
  sudo apt install unzip -y  
  unzip awscliv2.zip  
  sudo ./aws/install  

  Verified installation:

  aws --version

  Configured credentials:

  aws configure

  Entered:

  - Access Key ID
  - Secret Access Key
  - Region: ap-south-1

  Verified connectivity:

  aws ec2 describe-instances

  Empty reservations confirmed successful authentication.

  ---

  ## 🧱 Terraform Installation

  Installed Terraform:

  sudo apt install terraform -y  
  terraform --version

  Terraform environment prepared for Infrastructure as Code.

  ---

  ## 🌍 Global HTML Hosting Using Apache

  Installed Apache web server:

  sudo apt install apache2 -y  
  sudo systemctl start apache2  
  sudo systemctl enable apache2  

  Security Group inbound rules configured:

  SSH – Port 22 – Anywhere IPv4  
  HTTP – Port 80 – Anywhere IPv4  

  ---

  ## 📝 Creating HTML Page

  Edited default Apache index file:

  sudo nano /var/www/html/index.html

  Added:

  <!DOCTYPE html>
  <html>
  <head>
  <title>Sudharsan DevOps</title>
  </head>
  <body>
  <h1>Hello World</h1>
  <p>This page is hosted on AWS EC2.</p>
  <p>Deployed by Sudharsan.</p>
  </body>
  </html>

  Restarted Apache:

  sudo systemctl restart apache2

  Opened browser:

  http://PUBLIC_IP

  HTML page became globally accessible.

  ---

  ## ⚠️ SSH Troubleshooting

  Common issues encountered:

  - Instance stopped
  - Public IP changed after restart
  - SSH port blocked
  - IPv6 selected instead of IPv4

  Fixes:

  - Ensure instance Running
  - Copy new Public IPv4
  - Enable SSH Anywhere IPv4
  - Retry SSH

  ---

  ## 🧠 Key Concepts Learned

  1️⃣ EC2 Linux provisioning  
  2️⃣ SSH remote access  
  3️⃣ IAM admin permissions  
  4️⃣ AWS CLI authentication  
  5️⃣ Terraform preparation  
  6️⃣ Apache web hosting  
  7️⃣ Security Groups  
  8️⃣ Global IP based access  

  ---

  ## ✅ Outcome

  By the end of this session:

  - Ubuntu EC2 server launched
  - Connected via SSH from Windows
  - IAM admin user created
  - AWS CLI configured
  - Terraform installed
  - Apache web server deployed
  - HTML webpage hosted globally
  - Core DevOps cloud fundamentals understood

  This setup forms the foundation for Docker, Jenkins, Terraform automation, and CI/CD pipelines.


