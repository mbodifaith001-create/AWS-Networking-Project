🌐 AWS VPC Network Design & EC2 Web Server Deployment
Overview
This project demonstrates how to build a secure, multi‑AZ AWS Virtual Private Cloud (VPC) from scratch and deploy a functional Apache web server on an EC2 instance. The network includes public and private subnets, proper routing, NAT/IGW configuration, and a security‑hardened web server accessible over HTTP.

🏗️ Architecture
VPC
CIDR: 10.0.0.0/16

Name: Lab VPC

Subnets
Public Subnet 1: 10.0.0.0/24

Private Subnet 1: 10.0.1.0/24

Public Subnet 2: 10.0.2.0/24

Private Subnet 2: 10.0.3.0/24

Internet Connectivity
Internet Gateway (IGW) → Public subnets

NAT Gateway → Private subnets outbound access

Route Tables
Public Route Table → IGW

Private Route Table → NAT Gateway

Compute Layer
EC2 Instance: Amazon Linux 2, t3.micro

Subnet: Public Subnet 2

Security Group: HTTP (80) allowed from 0.0.0.0/0

User Data installs Apache + deploys sample app

🔧 Implementation Steps
1. VPC Foundation
Created VPC: 10.0.0.0/16

Used VPC wizard to generate initial subnets, IGW, NAT, and route tables.

2. Multi‑AZ Subnet Expansion
Added:

Public Subnet 2 → 10.0.2.0/24

Private Subnet 2 → 10.0.3.0/24

3. Routing Configuration
Public Subnet 2 → Public Route Table

Private Subnet 2 → Private Route Table

Public → IGW

Private → NAT Gateway

4. Security Group Setup
Inbound:

HTTP (80) → Anywhere (0.0.0.0/0)

All other traffic blocked by default.

5. EC2 Web Server Deployment
Launched EC2 with user data:

Code
#!/bin/bash
yum install -y httpd mysql php
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
unzip lab-app.zip -d /var/www/html/
chkconfig httpd on
service httpd start
✅ Validation
EC2 reached 2/2 status checks

Opened Public IPv4 DNS in browser

Web application loaded successfully over HTTP

🎯 Skills Demonstrated
VPC design & IPv4 subnetting

Public vs private subnet isolation

IGW vs NAT Gateway

Route table configuration

Security Group design

EC2 launch configuration

User‑data automation

Linux + Apache web server setup

👤 Author
Faith Felix Mbodi
Cloud Computing Practioner | AWS Learner | IT Student

