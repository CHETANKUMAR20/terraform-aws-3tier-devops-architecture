<p align="center">

<a href="https://github.com/CHETANKUMAR20/terraform-aws-3tier-devops-architecture">
  <img src="https://img.shields.io/badge/GitHub-Repository-black?logo=github" />
</a>

<img src="https://img.shields.io/github/actions/workflow/status/CHETANKUMAR20/terraform-aws-3tier-devops-architecture/terraform.yml?label=CI&logo=githubactions&logoColor=white" />

<img src="https://img.shields.io/badge/Terraform-v1.6+-623CE4?logo=terraform&logoColor=white" />

<img src="https://img.shields.io/badge/Cloud-AWS-orange?logo=amazonaws&logoColor=white" />

<img src="https://img.shields.io/badge/Deployment-SSH-blue" />

<img src="https://img.shields.io/badge/License-MIT-yellow" />

</p>

# 🚀 Terraform AWS 3-Tier DevOps Architecture (ap-south-1)

This project provisions a secure 3-tier architecture on AWS using Terraform in the **Mumbai Region (ap-south-1)**.

---

## 🏗 Architecture Diagram

![3-Tier AWS Architecture](docs/architecture/3-tier%20AWS%20architecture%20diagram.png)

---

# 📌 Infrastructure Overview

- VPC: 10.0.0.0/16
- Public Subnet (ap-south-1a)
- Private Subnet 1 (ap-south-1a)
- Private Subnet 2 (ap-south-1b)
- Internet Gateway
- Route Table (0.0.0.0/0 → IGW)
- EC2 Web Server (Public Subnet)
- RDS MySQL Database (Private Multi-AZ Subnet Group)

---

# 🔄 Terraform Execution Workflow

---

## 1️⃣ Terraform Initialization

```bash
terraform init
```

![Terraform Init](docs/screenshots/01-terraform-init-success.png)

---

## 2️⃣ Validate Configuration

```bash
terraform validate
```

![Terraform Validate](docs/screenshots/02-terraform-validate-success.png)

---

## 3️⃣ Apply Infrastructure

```bash
terraform apply
```

![Terraform Apply Execution](docs/screenshots/03-terraform-apply-execution.png)


## terraform apply : completed! ✔ 

![Terraform Apply Completed](docs/screenshots/07-terraform-apply-completed-successfully.png)

---

# 🌐 Networking Setup

---

## VPC Configuration

![VPC CIDR](docs/screenshots/14-vpc-cidr-details.png)
![VPC Overview](docs/screenshots/18-vpc-overview.png)

---

## Subnets (Public + Multi-AZ Private)

![Subnets Overview](docs/screenshots/15-subnets-public-private-overview.png)
![RDS Multi-AZ Subnets](docs/screenshots/10-rds-subnet-az-configuration.png)

---

## Internet Gateway

![Internet Gateway](docs/screenshots/17-internet-gateway-overview.png)
![IGW Attached](docs/screenshots/19-internet-gateway-attached.png)

---

## Route Table

![Route Table Public Access](docs/screenshots/16-route-table-public-internet-access.png)
![Route Table Association](docs/screenshots/20-route-table-association.png)

---

# 🔐 Security Groups

---

## EC2 Security Group

- Port 22 (SSH)
- Port 80 (HTTP)

![EC2 SG Rules](docs/screenshots/05-ec2-security-group-inbound-rules.png)
![EC2 SG Attached](docs/screenshots/22-ec2-security-group-attached.png)

---

## RDS Security Group

- Port 3306 allowed from EC2 Security Group only

![RDS SG Rules](docs/screenshots/21-rds-security-group-mysql-access.png)

---

# 🖥 EC2 Deployment

![EC2 Running](docs/screenshots/04-ec2-instance-running.png)

### SSH Verified

![EC2 SSH Success](docs/screenshots/11-ec2-ssh-connection-success.png)

---

# 🗄 RDS Deployment

- Engine: MySQL 8.0
- Instance Type: db.t3.micro
- Multi-AZ DB Subnet Group

![RDS Available](docs/screenshots/08-rds-instance-available-mysql.png)
![DB Subnet Group](docs/screenshots/09-rds-db-subnet-group-multi-az.png)

### Database Connectivity Verified

![RDS Connection Test](docs/screenshots/12-rds-database-connection-test.png)
![Database Created](docs/screenshots/13-rds-database-schema-created.png)

---

# 🧠 Real-World Debugging Experience

During implementation, the following issues were resolved:

### 1️⃣ Availability Zone Coverage Error
RDS required minimum 2 AZs for DB Subnet Group.

### 2️⃣ Instance Class Compatibility
db.t2.micro not supported with MySQL 8.0 in ap-south-1.

### 3️⃣ Password Policy Restriction
Special characters such as '/', '@', '"', and non-ASCII characters were rejected.

---

# 🧹 Infrastructure Cleanup

```bash
terraform destroy
```

![Terraform Destroy](docs/screenshots/23-terraform-destroy-success.png)

---

# ✅ Key Skills Demonstrated

- Infrastructure as Code (Terraform)
- AWS VPC & Subnet Architecture
- Multi-AZ Database Deployment
- Secure Security Group Referencing
- Debugging AWS API Errors
- Cloud Infrastructure Lifecycle Management

---

---
Built using Terraform and AWS.
