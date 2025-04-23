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
4. Enable CloudWatch Logs
Ensure the CloudTrail is delivering logs to a CloudWatch Log Group.

5. Create a Metric Filter
Log Group: Select the one from your trail

Filter Pattern: "GetSecretValue"

Metric Namespace: securitymetric

Metric Name: secret_accessed

Metric Value: 1

Default Value: 0

6. Create a CloudWatch Alarm
Metric: securitymetric:secret_accessed

Condition: Static threshold ≥ 1

Action: Send notification to an SNS topic

7. Create SNS Topic
Create a topic (e.g. SecretAccessAlert)

Subscribe your email

Confirm the subscription

8. Test Notification
Access the secret again in Secrets Manager

You should receive an email notification from SNS 🎉

📈 Result
✅ Secret access is tracked via CloudTrail
✅ Log events filtered in CloudWatch
✅ Metrics generated and monitored
✅ Alarms triggered and notifications sent via SNS
