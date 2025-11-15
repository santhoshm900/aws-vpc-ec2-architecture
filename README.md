# aws-vpc-ec2-architecture
Custom AWS VPC architecture with public subnet, Internet Gateway, route table, security group, and EC2 instance. Includes network diagram built using draw.io for understanding basic AWS networking.
![AWS VPC Architecture](aws-vpc-ec2-architecture.png)
# 🚀 AWS VPC + EC2 Architecture

A complete and beginner-friendly AWS networking project designed to understand VPC, Subnet, Route Tables, Internet Gateway, Security Groups, and EC2 setup.  
Built using **AWS Console + Draw.io**, perfect for learning and portfolio demonstration.

---

## 🏗️ Architecture Diagram

<img src="./diagrams/aws-vpc-ec2-architecture.png" width="700">

---

## 📂 Project Structure

```
root/
│
├── diagrams/                     # All VPC, EC2 & networking images
│   ├── aws-vpc-ec2-architecture.png
│   ├── ec2-instance-running.png
│   ├── internet-gateway.png
│   ├── route-table-created.png
│   ├── route-table-subnet-association.png
│   ├── subnet-created.png
│   ├── vpc-created.png
│   └── nginx-service-running.png
│
├── docs/
│   └── architecture-explanation.md   # Full documentation of the design
│
└── README.md
```
1️⃣ Create a VPC

Go to AWS Console → VPC

Create VPC

Name: net-vpc

CIDR: 10.0.0.0/16

2️⃣ Create Public Subnet

Go to Subnets → Create Subnet

Select your VPC

Subnet CIDR: 10.0.0.0/24

Availability Zone: ap-south-1a

Enable Auto-assign Public IP

3️⃣ Create Internet Gateway

Go to Internet Gateways → Create

Attach to your VPC (net-vpc)

4️⃣ Route Table Setup

Create Route Table

Name: public-route-table

Associate with your Subnet

Add route:

0.0.0.0/0 → Internet Gateway

5️⃣ Create Security Group

Rules to allow:

HTTP: 80

HTTPS: 443

SSH: 22

6️⃣ Launch EC2 Instance

AMI: Amazon Linux 2

Instance type: t2.micro

Subnet: public subnet

Security Group: your SG

Click Create key pair

Key pair type: RSA

File format: .pem

Download the .pem file
(This file is required for SSH login)

🔄 2. Convert .pem → .ppk (for PuTTY users)

If you are using PuTTY, convert .pem to .ppk:

Open PuTTYgen

Click Load

Select your .pem file
(choose All Files*)

Click Save private key

Save it as .ppk
(Used for Windows PuTTY SSH login)

🖥️ 3. Login to EC2 using SSH
➡️ If using PuTTY (Windows)

Open PuTTY

Hostname:

13.233.165.191


Go to SSH → Auth

Browse & attach your .ppk key

Click Open

7️⃣ Install & Start Nginx

SSH into EC2:

sudo yum update -y
sudo amazon-linux-extras install nginx1 -y
sudo systemctl enable nginx
sudo systemctl start nginx

8️⃣ Test the Website

Open:

http://13.233.165.191


You should see: Welcome to Nginx!


