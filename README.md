<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EC2 Instance Automation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            color: #333;
            margin: 20px;
            padding: 20px;
            border-radius: 10px;
        }
        h1, h2, h3 {
            color: #2c3e50;
        }
        code {
            background-color: #eaeaea;
            padding: 5px;
            border-radius: 5px;
            display: block;
            margin: 10px 0;
        }
        .container {
            max-width: 800px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>✨ EC2 Instance Automation using AWS Lambda & CloudWatch</h1>
        
        <h2>✨ Description</h2>
        <p>This project automates the start/stop of EC2 instances using AWS Lambda, CloudWatch, and other AWS services. It helps reduce costs by shutting down instances during idle hours.</p>
        
        <h2>🛠️ Services Used</h2>
        <ul>
            <li><b>EC2</b> - Virtual Machines</li>
            <li><b>IAM</b> - Permissions Management</li>
            <li><b>Lambda</b> - Automation of Start/Stop</li>
            <li><b>Amazon EventBridge</b> - Scheduling</li>
            <li><b>SNS</b> - Email Notifications</li>
            <li><b>CloudWatch</b> - Log Monitoring</li>
        </ul>
        
        <h2>🔧 Setup Instructions</h2>
        
        <h3>1️⃣ EC2 Instances Setup</h3>
        <p>Create 6 EC2 instances with the required specifications.</p>
        
        <h3>2️⃣ IAM Role Setup</h3>
        <p>Create an IAM role with these policies:</p>
        <ul>
            <li>AmazonEC2FullAccess</li>
            <li>AmazonEventBridgeFullAccess</li>
            <li>AmazonSNSFullAccess</li>
            <li>CloudWatchFullAccess</li>
        </ul>
        
        <h3>3️⃣ Lambda Function</h3>
        <p>Create a Lambda function that starts & stops EC2 instances.</p>
        
        <h4>Start EC2 Instances</h4>
        <code>
import boto3
import os

ec2 = boto3.client('ec2')
sns = boto3.client('sns')

def lambda_handler(event, context):
    instance_ids = ['put instance_ids']  
    ec2.start_instances(InstanceIds=instance_ids)
    sns.publish(TopicArn=os.environ['SNS_TOPIC_ARN'], Message=f"EC2 Instances {'put instance_ids'} have been started.")
    return {"message": "EC2 instances started successfully"}
        </code>
        
        <h4>Stop EC2 Instances</h4>
        <code>
import boto3
import os

ec2 = boto3.client('ec2')
sns = boto3.client('sns')

def lambda_handler(event, context):
    instance_ids = ['put instance_ids']
    ec2.stop_instances(InstanceIds=instance_ids)
    sns.publish(TopicArn=os.environ['SNS_TOPIC_ARN'], Message=f"EC2 Instances {'put instance_ids'} have been stopped.")
    return {"message": "EC2 instances stopped successfully"}
        </code>
        
        <h3>4️⃣ EventBridge Rules Setup</h3>
        <p>Create rules to trigger Lambda functions:</p>
        <ul>
            <li><b>Start Instances (9 AM IST):</b> <code>cron(30 3 * * ? *)</code></li>
            <li><b>Stop Instances (6 PM IST):</b> <code>cron(30 12 * * ? *)</code></li>
        </ul>
        
        <h3>5️⃣ SNS for Email Notifications</h3>
        <p>Create an SNS Topic to receive instance status updates.</p>
    </div>
</body>
</html>
