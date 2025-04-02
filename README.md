# 🚀 EC2 Instance Automation using AWS Lambda and CloudWatch

## 📌 Overview
This project automates the starting and stopping of EC2 instances using AWS Lambda, CloudWatch, and related AWS services. The goal is to optimize cost efficiency by scheduling EC2 instances to run only when needed.

## 🛠️ Services Used
- **Amazon EC2** - Virtual Machines for compute power.
- **IAM** - Role-based access control and permissions.
- **AWS Lambda** - Serverless compute for automation.
- **Amazon EventBridge** - Scheduler for triggering Lambda functions.
- **Amazon SNS** - Notifications for instance status updates.
- **Amazon CloudWatch** - Logs and monitoring.

## 🔧 Setup Instructions
### 1️⃣ EC2 Instances Configuration
- Launch **6 EC2 instances** with required configurations in AWS.
- Ensure proper security groups and key pairs are configured.

### 2️⃣ IAM Role Setup
- Create an **IAM Role** with the following policies:
  - `AmazonEC2FullAccess`
  - `AmazonEventBridgeFullAccess`
  - `AmazonSNSFullAccess`
  - `CloudWatchFullAccess`

### 3️⃣ Lambda Function
- Create a **Lambda function** to automate the start/stop of EC2 instances.
- Attach the **IAM Role** created earlier.
- Set environment variables for **SNS Topic ARN** to enable notifications.

### 4️⃣ Amazon EventBridge Rules
- Schedule EventBridge rules to trigger the Lambda function.
- **Start Instances (9 AM IST):** `cron(30 3 * * ? *)`
- **Stop Instances (6 PM IST):** `cron(30 12 * * ? *)`

### 5️⃣ SNS for Email Notifications
- Create an **SNS Topic** and subscribe your email to receive instance status updates.
- Ensure SNS permissions allow Lambda to publish notifications.

## 📌 Key Benefits
✅ **Cost Optimization** - Automatically shuts down instances when not in use.  
✅ **Scalability** - Easily manage multiple EC2 instances with automation.  
✅ **Serverless & Hassle-Free** - No infrastructure management required for automation.  
✅ **Real-time Notifications** - Get notified when instances start or stop.  

---

🎯 **Want to contribute?** Feel free to fork and submit a pull request! 💡
