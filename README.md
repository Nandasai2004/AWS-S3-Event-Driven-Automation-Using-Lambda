# ⚡ AWS S3 Event-Driven Automation Using Lambda

## 📌 Project Overview

This project demonstrates event-driven automation using **Amazon S3 and AWS Lambda**. Whenever a file is uploaded to an Amazon S3 bucket, an event triggers an AWS Lambda function to process the uploaded file automatically.

## 🎯 Project Objective

To automatically trigger an AWS Lambda function whenever a file is uploaded to an Amazon S3 bucket.

## 🛠️ Technologies Used

- **Amazon S3** – Stores uploaded files.
- **AWS Lambda** – Executes code in response to events.
- **AWS IAM** – Manages permissions and execution roles.
- **Amazon CloudWatch** – Monitors Lambda execution logs.
- **Python** – Implements the Lambda function.

## 🏗️ Architecture

```text
        User Uploads a File
                 |
                 v
           Amazon S3 Bucket
                 |
                 v
         S3 Object-Created Event
                 |
                 v
          AWS Lambda Function
                 |
                 v
       Process Uploaded File
                 |
                 v
       Amazon CloudWatch Logs
```

## 🚀 Implementation Steps

### Step 1: Create an S3 Bucket
- Open the AWS Management Console.
- Navigate to Amazon S3.
- Create a new bucket to store uploaded files.

### Step 2: Configure IAM Permissions
- Create an IAM role for the Lambda function.
- Attach the required Lambda execution permissions.
- Configure the permissions needed to access S3 objects.

### Step 3: Create an AWS Lambda Function
- Open AWS Lambda.
- Create a function using Python.
- Configure the execution role.
- Add code to handle S3 event notifications.

### Step 4: Configure the S3 Event Trigger
- Open the S3 bucket's Properties tab.
- Create an event notification.
- Select the object-created event.
- Connect the event notification to the Lambda function.

### Step 5: Test the Automation
- Upload a file to the S3 bucket.
- Verify that the Lambda function is triggered.
- Check the execution output and logs in Amazon CloudWatch.

## 💻 Lambda Function Example

```python
def lambda_handler(event, context):
    for record in event.get("Records", []):
        bucket = record["s3"]["bucket"]["name"]
        key = record["s3"]["object"]["key"]

        print("S3 Event Triggered Successfully!")
        print(f"Bucket Name: {bucket}")
        print(f"Uploaded File: {key}")

    return {
        "statusCode": 200,
        "body": "File upload processed successfully"
    }
```

## 📊 Expected Result

When a file is uploaded to the configured S3 bucket:

1. Amazon S3 generates an object-created event.
2. AWS Lambda receives the event.
3. The function extracts the bucket name and uploaded file name.
4. Execution details are recorded in CloudWatch Logs.

## 📚 Key Learnings

- Understanding event-driven architecture in AWS.
- Creating and configuring S3 buckets.
- Developing AWS Lambda functions using Python.
- Configuring IAM execution roles and permissions.
- Integrating S3 event notifications with Lambda.
- Monitoring function execution through CloudWatch.

## 🔐 Security Best Practices

- Follow the principle of least privilege for IAM roles.
- Grant access only to the required S3 resources.
- Avoid storing credentials directly in source code.
- Monitor Lambda execution logs and errors.

## 👨‍💻 Author

**Gorlamandala Nanda Sai**

B.Tech – Artificial Intelligence and Machine Learning

GitHub: [@Nandasai2004](https://github.com/Nandasai2004)

## ⭐ Conclusion

This project demonstrates how Amazon S3 event notifications can automatically invoke AWS Lambda functions, reducing manual work and enabling scalable, event-driven cloud automation.
