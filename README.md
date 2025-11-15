# aws-vpc-ec2-architecture
Custom AWS VPC architecture with public subnet, Internet Gateway, route table, security group, and EC2 instance. Includes network diagram built using draw.io for understanding basic AWS networking.
![AWS VPC Architecture](aws-vpc-ec2-architecture.png)
# 🚀 AWS VPC + EC2 Architecture

A complete and beginner-friendly AWS networking project designed to understand VPC, Subnet, Route Tables, Internet Gateway, Security Groups, and EC2 setup.  
Built using **AWS Console + Draw.io**, perfect for learning and portfolio demonstration.

---

## 🖼️ Architecture Diagram  

<p align="center">
<img src="diagrams/aws-vpc-ec2-architecture.png" width="750">

</p>

---
---

## 🖼️ Individual Diagram Steps

### 1️⃣ VPC Created
<img src="diagrams/vpc-created.png" width="600">

### 2️⃣ Subnet Created
<img src="diagrams/subnet-created.png" width="600">

### 3️⃣ Route Table Created
<img src="diagrams/route-table-created.png" width="600">

### 4️⃣ Route Table – Subnet Association
<img src="diagrams/route-table-subnet-association.png" width="600">

### 5️⃣ Internet Gateway Created
<img src="diagrams/internet-gateway.png" width="600">

### 6️⃣ IGW Attached to VPC
<img src="diagrams/igw.png" width="600">

### 7️⃣ EC2 Instance Running
<img src="diagrams/ec2-instance-running.png" width="600">

### 8️⃣ Nginx Running Screenshot
<img src="diagrams/nginx-service-running.png" width="600">




## 🚀 Steps to Create the Architecture

---

### **1️⃣ Create a VPC**
- Go to **AWS Console → VPC**
- Click **Create VPC**
- Name: `net-vpc`
- CIDR: `10.0.0.0/16`

---

### **2️⃣ Create Public Subnet**
- Go to **Subnets → Create Subnet**
- Select VPC: `net-vpc`
- Subnet CIDR: `10.0.0.0/24`
- Availability Zone: `ap-south-1a`
- Enable **Auto-assign Public IP**

---

### **3️⃣ Create Internet Gateway**
- Go to **Internet Gateways → Create**
- Attach the IGW to `net-vpc`

---

### **4️⃣ Route Table Setup**
- Create Route Table → Name: `public-route-table`
- Associate with **public subnet**
- Add route:
  ```
  0.0.0.0/0 → Internet Gateway
  ```

---

### **5️⃣ Create Security Group**
Allow inbound rules:
- HTTP → 80  
- HTTPS → 443  
- SSH → 22  

---

### **6️⃣ Launch EC2 Instance**
- AMI: **Amazon Linux 2**
- Instance type: **t2.micro**
- Subnet: **Public Subnet**
- Security Group: your SG

---

## 🔑 **7️⃣ Create Key Pair**

### Create & Download `.pem` file
- Click **Create key pair**
- Key type: **RSA**
- File type: **.pem**
- Download `.pem` (very important)

---

## 🔄 **Convert `.pem` → `.ppk` (PuTTY users only)**

1. Open **PuTTYgen**
2. Click **Load**
3. Select your **.pem** file (choose *All Files*)
4. Click **Save private key**
5. Save as **.ppk**

---

## 🖥️ **8️⃣ Login to EC2 via SSH**

### ▶️ If using PuTTY (Windows)
- Open **PuTTY**
- Hostname:
  ```
  ec2-user@13.233.165.191
  ```
- Go to **SSH → Auth**
- Browse & select your `.ppk` key
- Click **Open**

---

## 🔧 **9️⃣ Install & Start Nginx**

SSH into EC2 and paste this:

```bash
sudo yum update -y
sudo amazon-linux-extras install nginx1 -y
sudo systemctl enable nginx
sudo systemctl start nginx
```

---

## 🌍 **🔟 Test the Website**

Open this in browser:

```
http://<public ip>
```

You should see:

**Welcome to Nginx!**

