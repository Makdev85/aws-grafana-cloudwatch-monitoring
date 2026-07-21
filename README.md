# AWS CloudWatch Monitoring with Grafana Cloud

## 📌 Project Overview

This project demonstrates how to monitor an Amazon EC2 instance using **Amazon CloudWatch** and **Grafana Cloud**. The monitoring dashboard provides real-time insights into EC2 performance metrics, and an alert rule sends an email notification whenever CPU utilization exceeds a defined threshold.

---

# 🏗️ Architecture

```
                    +----------------------+
                    |    Amazon EC2        |
                    +----------+-----------+
                               |
                               | Performance Metrics
                               ▼
                    +----------------------+
                    |  Amazon CloudWatch   |
                    +----------+-----------+
                               |
                               | CloudWatch Data Source
                               ▼
                    +----------------------+
                    |    Grafana Cloud     |
                    +----------+-----------+
                               |
                +--------------+--------------+
                |                             |
                ▼                             ▼
        Monitoring Dashboard          Alert Rules
                                              |
                                              ▼
                                   Email Notification
```

---

# 🛠️ AWS Services Used

- Amazon EC2
- AWS IAM
- Amazon CloudWatch
- Grafana Cloud

---

# 📋 Prerequisites

Before starting, make sure you have:

- AWS Account
- Running EC2 Instance
- Grafana Cloud Account
- IAM User with CloudWatch permissions

---

# 🚀 Implementation Steps

## Step 1: Launch an EC2 Instance

- Launch an EC2 instance.
- Choose Amazon Linux 2023 or Ubuntu.
- Configure Security Groups.
- Verify the instance is in the **Running** state.

**Screenshot**

`screenshots/01-ec2-instance.png`

---

## Step 2: Create an IAM User

- Open AWS IAM.
- Create a new IAM User.
- Attach the following policies:
  - CloudWatchFullAccess
  - AmazonEC2FullAccess
- Generate an Access Key and Secret Access Key.

**Screenshot**

`screenshots/02-iam-user.png`

---

## Step 3: Configure Grafana Cloud

- Log in to Grafana Cloud.
- Navigate to **Connections → Data Sources**.
- Add **Amazon CloudWatch**.
- Enter:
  - Access Key
  - Secret Access Key
  - Default Region
- Click **Save & Test**.

**Screenshot**

`screenshots/03-cloudwatch-datasource.png`

---

## Step 4: Create an EC2 Monitoring Dashboard

- Create a new dashboard.
- Add a visualization.
- Select:
  - Namespace: **AWS/EC2**
  - Metric: **CPUUtilization**
  - Statistic: **Maximum**
  - Dimension: **InstanceId**

**Screenshot**

`screenshots/04-dashboard.png`

---

## Step 5: Monitor EC2 Metrics

The dashboard displays:

- CPU Utilization
- Network In
- Network Out
- Status Checks

**Screenshot**

`screenshots/05-cpu-metrics.png`

---

## Step 6: Configure Alert Rule

Create a Grafana-managed alert.

Configuration:

- Metric: CPUUtilization
- Threshold: Greater than **80%**
- Evaluation Interval: **1 minute**
- Pending Period: **5 minutes**

**Screenshot**

`screenshots/06-alert-rule.png`

---

## Step 7: Configure Email Notifications

- Create an Email Contact Point.
- Configure the Notification Policy.
- Test the Email Contact Point.

---

## Step 8: Test the Alert

Generate CPU load on the EC2 instance.

Amazon Linux

```bash
sudo yum install stress -y
stress --cpu 2 --timeout 300
```

Ubuntu

```bash
sudo apt update
sudo apt install stress -y
stress --cpu 2 --timeout 300
```

Verify:

- Alert Status changes to **Firing**
- Email notification is received successfully.

**Screenshots**

`screenshots/07-alert-firing.png`

`screenshots/08-email-notification.png`

---

# 📸 Project Screenshots

| Screenshot | Description |
|------------|-------------|
| 01 | EC2 Instance |
| 02 | IAM User |
| 03 | CloudWatch Data Source |
| 04 | Grafana Dashboard |
| 05 | EC2 Metrics |
| 06 | Alert Rule |
| 07 | Alert Firing |
| 08 | Email Notification |

---

# ✅ Results

- Successfully connected Grafana Cloud to Amazon CloudWatch.
- Created a real-time EC2 monitoring dashboard.
- Configured CPU utilization alerts.
- Verified email notifications on threshold breach.
- Built a complete cloud monitoring workflow.

---

# 💡 Skills Demonstrated

- Amazon EC2
- AWS IAM
- Amazon CloudWatch
- Grafana Cloud
- Cloud Monitoring
- Dashboard Creation
- Alert Management
- Email Notifications
- Infrastructure Monitoring

---

# 📚 Conclusion

This project demonstrates how to build a cloud monitoring and alerting solution using AWS CloudWatch and Grafana Cloud. The solution provides real-time infrastructure monitoring and automated email notifications for performance events, making it suitable for production monitoring and DevOps workflows.

---

## 👨‍💻 Author

**Mohammed Mustafa Ali Khan**

GitHub: https://github.com/MohammedMustafaAliKhan85
