AWS RDS Database Deployment & SQL Management (Aurora/MySQL)

Overview

This project demonstrates how to deploy a fully managed relational database using Amazon RDS (Aurora/MySQL) and connect to it securely from an Amazon EC2 Linux instance. It includes database design, SQL operations, and relational joins to showcase cloud database administration skills.

Features
AWS RDS (Aurora/MySQL) deployment
Secure EC2-to-RDS connectivity
MariaDB/MySQL client installation
Database schema design
SQL data insertion & retrieval
INNER JOIN operations
VPC & Security Group configuration

Architecture
User
   │
   ▼
SSH
   │
Amazon EC2 (Linux)
   │
MariaDB/MySQL Client
   │
Amazon RDS (Aurora/MySQL)
   │
SQL Database

Implementation Steps
1. Provision RDS (Aurora/MySQL)
Dev/Test template

db.t3.micro instance

General Purpose SSD

Lab VPC

Security Group configuration

2. Configure Secure Connectivity
Updated inbound rules to allow EC2 access

Connected to EC2 via SSH

Installed MariaDB client:
Code
sudo yum install mariadb -y

3. Connect to RDS
Code
mysql -u admin -p -h <RDS-ENDPOINT>

4. Database Design
Code
CREATE DATABASE student_records;
USE student_records;
CREATE TABLE RESTART (
  StudentID INT PRIMARY KEY,
  StudentName VARCHAR(100),
  RestartCity VARCHAR(100),
  GraduationDate DATETIME
);

CREATE TABLE CLOUD_PRACTITIONER (
  StudentID INT,
  CertificationDate DATE,
  FOREIGN KEY (StudentID) REFERENCES RESTART(StudentID)
);

5. Data Management
Inserted sample records and retrieved data using SQL queries:
Code
SELECT * FROM RESTART;

7. SQL Join Operation
Code
SELECT
  R.StudentID,
  R.StudentName,
  C.CertificationDate
FROM RESTART R
INNER JOIN CLOUD_PRACTITIONER C
ON R.StudentID = C.StudentID;
Key Skills Demonstrated
AWS Cloud Infrastructure

RDS & EC2 configuration

VPC networking & security groups

SQL (DDL, DML, Joins)

Linux command-line operations

Secure cloud database administration

Project Outcome
Successfully deployed a cloud-hosted relational database, configured secure EC2-to-RDS connectivity, designed normalized tables, inserted sample data, and executed SQL joins to retrieve meaningful insights.


Author:
Faith Felix Mbodi  
Cloud Computing Practioner | AWS Learner | IT Student
