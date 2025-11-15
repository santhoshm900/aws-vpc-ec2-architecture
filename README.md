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

---

## 🚀 Steps to Create the Architecture

### **1️⃣ Create a VPC**
- Go to **AWS Console → VPC**
- Create VPC  
  - Name: `net-vpc`  
  - CIDR: `10.0.0.0/16`

---

### **2️⃣ Create Public Subnet**
- Go to **Subnets → Create Subnet**
- Select VPC: `net-vpc`
- Subnet CIDR: `10.0.0.0/24`
- AZ: `ap-south-1a`
- Enable **Auto-assign Public IP**

---

### **3️⃣ Create Internet Gateway**
- Go to **Internet Gateways → Create**
- Attach to `net-vpc`

---

### **4️⃣ Route Table Setup**
- Create Route Table → `public-route-table`
- Associate with **public subnet**
- Add route:
  - `0.0.0.0/0 → Internet Gateway`

---

### **5️⃣ Create Security Group**
Allow inbound rules:
- HTTP (80)  
- HTTPS (443)  
- SSH (22)  

---

### **6️⃣ Launch EC2 Instance**
- AMI: **Amazon Linux 2**
- Instance type: **t2.micro**
- Subnet: **Public Subnet**
- Security Group: your SG

---

## 🔑 7️⃣ Create Key Pair

### **Create & Download .pem**
- Click **Create key pair**
- Key pair type: **RSA**
- File format: **.pem**
- Download `.pem` file (IMPORTANT)

---

## 🔄 Convert `.pem` → `.ppk` (for PuTTY)
1. Open **PuTTYgen**
2. Click **Load**
3. Select your `.pem` file (choose *All Files*)
4. Click **Save private key**
5. Save as **`.ppk`**

---

## 🖥️ 8️⃣ Login to EC2 via SSH

### ▶️ **If using PuTTY (Windows)**
- Open **PuTTY**
- Hostname:
  ```
  ec2-user@13.233.165.191
  ```
- Go to **SSH → Auth → Browse**
- Select your `.ppk` key
- Click **Open**

---

## 🔧 9️⃣ Install & Start Nginx

SSH into EC2 and run:

```bash
sudo yum update -y
sudo amazon-linux-extras install nginx1 -y
sudo systemctl enable nginx
sudo systemctl start nginx
```

---

## 🌍 🔟 Test the Website

Open:

```
http://13.233.165.191
```

You should see:

**Welcome to Nginx!**
