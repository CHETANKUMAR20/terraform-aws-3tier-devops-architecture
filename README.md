# 🚀 Terraform AWS 3-Tier DevOps Architecture (ap-south-1)

This project demonstrates how to provision a secure 3-tier architecture on AWS using Terraform.

The infrastructure includes:
- VPC
- Public and Private Subnets (Multi-AZ)
- Internet Gateway
- Route Tables
- Security Groups
- EC2 Web Server (Public Subnet)
- RDS MySQL Database (Private Subnets)

Region Used: **ap-south-1 (Mumbai)**

---

## 🏗 Architecture Overview

- VPC: 10.0.0.0/16
- Public Subnet: ap-south-1a
- Private Subnet 1: ap-south-1a
- Private Subnet 2: ap-south-1b
- EC2 in Public Subnet
- RDS in Private Subnet (Multi-AZ Subnet Group)

---

# 🔄 Terraform Workflow

---

## Step 1: Terraform Initialization

```bash
terraform init
```

📸 Screenshot:
`01-terraform-init-success.png`

---

## Step 2: Validate Configuration

```bash
terraform validate
```

📸 Screenshot:
`02-terraform-validate-success.png`

---

## Step 3: Apply Infrastructure

```bash
terraform apply
```

📸 Screenshot:
`03-terraform-apply-execution.png`  
📸 Screenshot:
`07-terraform-apply-completed-successfully.png`

---

# 🌐 VPC & Networking Setup

---

## VPC Configuration

- CIDR: 10.0.0.0/16

📸 Screenshot:
`14-vpc-cidr-details.png`  
`18-vpc-overview.png`

---

## Subnets Configuration

- 1 Public Subnet
- 2 Private Subnets (Multi-AZ)

📸 Screenshot:
`15-subnets-public-private-overview.png`  
`10-rds-subnet-az-configuration.png`

---

## Internet Gateway

📸 Screenshot:
`17-internet-gateway-overview.png`  
`19-internet-gateway-attached.png`

---

## Route Table Configuration

- Public Route: 0.0.0.0/0 → IGW

📸 Screenshot:
`16-route-table-public-internet-access.png`  
`20-route-table-association.png`

---

# 🔐 Security Configuration

---

## EC2 Security Group

- SSH (22)
- HTTP (80)

📸 Screenshot:
`05-ec2-security-group-inbound-rules.png`  
`22-ec2-security-group-attached.png`

---

## RDS Security Group

- MySQL (3306) allowed from EC2 Security Group only

📸 Screenshot:
`21-rds-security-group-mysql-access.png`

---

# 🖥 EC2 Instance

- Instance Type: t2.micro
- Public IP enabled
- Deployed in Public Subnet

📸 Screenshot:
`04-ec2-instance-running.png`

### SSH Access Verified

📸 Screenshot:
`11-ec2-ssh-connection-success.png`

---

# 🗄 RDS Database (MySQL)

- Engine: MySQL 8.0
- Instance Class: db.t3.micro
- Multi-AZ Subnet Group
- Private Access Only

📸 Screenshot:
`08-rds-instance-available-mysql.png`  
`09-rds-db-subnet-group-multi-az.png`

### Database Connection Verified

📸 Screenshot:
`12-rds-database-connection-test.png`  
`13-rds-database-schema-created.png`

---

# 🧠 Challenges Faced & Resolved

## 1️⃣ AZ Coverage Error
RDS requires minimum 2 Availability Zones for DB Subnet Group.

Solution:
Created second private subnet in ap-south-1b.

---

## 2️⃣ DB Instance Class Compatibility Error
db.t2.micro not supported with MySQL 8.0 in ap-south-1.

Solution:
Changed instance class to db.t3.micro.

---

## 3️⃣ Password Policy Error
RDS does not allow special characters such as '/', '@', '"', space, or non-ASCII characters.

Solution:
Used valid password format with allowed characters (e.g., Admin12345!)

---

# 🧹 Destroy Infrastructure

After testing, infrastructure was destroyed to avoid charges.

```bash
terraform destroy
```

📸 Screenshot:
`23-terraform-destroy-success.png`

---

# ✅ Key Learnings

- Infrastructure as Code using Terraform
- Multi-AZ RDS deployment
- VPC and subnet architecture
- Security Group referencing
- AWS API error debugging
- State management and plan execution

---

# 📌 Author

Chetan Kumar  
Cloud & DevOps Engineer (Aspirant)
