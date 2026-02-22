# aws-windows-erp-sql-deployment
End-to-end AWS deployment of Windows Server ERP infrastructure with SQL Server, secure remote access, automated backups, monitoring, and cost optimization.

# AWS Windows Server ERP Deployment for a SMB client

## Project Overview

This project demonstrates the end-to-end deployment of a secure, scalable, and cost-optimized Windows Server-based ERP infrastructure on Amazon Web Services (AWS).

The solution was implemented as a greenfield deployment to replace on-premise infrastructure and enable secure multi-user remote ERP access for 10–15 concurrent users.

---

## Business Objective

- Migrate ERP workload from local infrastructure to AWS
- Enable secure remote access for multiple users
- Implement automated backup and disaster recovery
- Ensure monitoring and alerting
- Optimize infrastructure cost through automation

---

## Architecture Summary
![Architecture Diagram](https://github.com/avinashsinghhub/aws-windows-erp-sql-deployment/blob/b0605577d40530fcfb74bed9849f4c9d170843e4/architecture/architecture-diagram.png)

The infrastructure includes:

- Amazon VPC (10.0.0.0/16)
- Public Subnet (10.0.1.0/24)
- Internet Gateway
- Amazon EC2 (Windows Server 2022 – m5.xlarge)
- SQL Server Web Edition
- 200GB gp3 Encrypted EBS Volume
- TSplus Remote Application Portal (HTTPS)
- AWS Backup (EBS Snapshots)
- Amazon S3 (SQL Backups – Intelligent-Tiering)
- Amazon CloudWatch (Monitoring & Alerts)
- Amazon EventBridge (Automated Start/Stop Scheduling)
- IAM Role for Systems Manager & Monitoring

---

## Network Configuration

- Dedicated VPC with DNS resolution enabled
- Public subnet for EC2 deployment
- Internet Gateway attached
- Route table configured for internet access
- Security Group with restricted access:
  - RDP (3389) – Office Public IP only
  - SQL (1433) – Office Public IP only
  - HTTPS (443) – TSplus Web Portal

---

## Compute & Storage Configuration

- Instance Type: m5.xlarge
- vCPU: 4
- RAM: 16 GB
- OS: Windows Server 2022
- Storage: 200GB gp3 (Encrypted)
- Delete on Termination: Enabled
- IAM Role Attached for SSM & Monitoring

---

## SQL Server Deployment

- SQL Server Web Edition installed
- ERP database configured
- SQL authentication enabled
- ERP application successfully connected and tested

---

## Secure Application Access (TSplus)

To avoid exposing full Windows desktop access:

- TSplus Remote Access installed
- Application-only publishing enabled
- 12 user accounts created
- Desktop access disabled
- HTTPS portal enabled
- SSL configured
- Controlled session access

Users access ERP securely via browser without full system exposure.

---

## Backup & Disaster Recovery Strategy

### 1. EBS Snapshots (AWS Backup)

- Daily automated backup plan
- Dedicated backup vault
- Lifecycle transition to cold storage
- Resource tagging for backup assignment

### 2. SQL Native Backups to S3

- S3 bucket with public access blocked
- Intelligent-Tiering enabled
- SQL .bak files uploaded regularly
- Long-term cost optimization

---

## Monitoring & Alerting

- CloudWatch CPU utilization alarms (>70%)
- Optional disk & memory monitoring via CloudWatch Agent
- SNS notification integration
- Systems Manager enabled via IAM Role

---

## Automated Cost Optimization

- EventBridge start schedule (08:30 IST, Mon–Fri)
- EventBridge stop schedule (18:30 IST, Mon–Fri)
- Reduced compute cost outside business hours
- gp3 storage selected for cost-performance balance
- Intelligent-Tiering storage for backups

---

## Security Posture

- Restricted RDP and SQL access
- IAM role-based management
- Encrypted EBS volumes
- Encrypted backup vault
- S3 public access blocked
- HTTPS enforced for ERP portal

---

## Deployment Outcome

The ERP environment is fully operational with:

- Secure remote access for 12 users
- Automated daily backups
- Cloud monitoring and alerts
- Scheduled cost control automation
- Encrypted storage and backup
- Controlled application-level access

---

## Skills Demonstrated

- AWS Infrastructure Architecture
- Windows Server Deployment on AWS
- SQL Server Configuration
- Backup & Disaster Recovery Planning
- Secure Remote Access Design
- Cloud Monitoring & Alerting
- Cost Optimization Strategy
- IAM & Security Best Practices
