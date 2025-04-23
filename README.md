# Security-Monitoring-Alerting-System-Using-AWS

# 🔐 Security Monitoring & Alerting System Using AWS

This project demonstrates a simple yet effective security monitoring and alerting system to track access to sensitive secrets stored in **AWS Secrets Manager**, using **CloudTrail**, **CloudWatch Logs**, **CloudWatch Alarms**, and **SNS Notifications**.

---

## 🚀 Overview

This system helps detect unauthorized or unexpected access to secrets and triggers alerts via email when someone retrieves secret values.

---

## 🛠️ AWS Services Used

- **AWS Secrets Manager**
- **AWS CloudTrail**
- **Amazon CloudWatch Logs**
- **Amazon CloudWatch Metrics & Alarms**
- **Amazon SNS**
- **AWS CLI**

---

## 📋 Setup Steps

### 1. Create a Secret
- Name: `secrete`
- Description: `A secrete created for security monitoring system.`
- Encryption Key: `aws/secretsmanager`

### 2. Enable CloudTrail
- Trail name: `secrete-manager`
- Multi-region: Enabled ✅
- Log file validation: Enabled ✅
- Log location: `secrete-manager-d/AWSLogs/<Account-ID>`
- Management Events:
  - API Activity: All
  - Exclude KMS & RDS Data API: Yes

### 3. Verify CloudTrail Logging
Run:
```bash
aws secretsmanager get-secret-value --secret-id "secrete" --region ap-south-1
