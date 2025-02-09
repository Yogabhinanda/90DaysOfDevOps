# AWS EC2 and Security Groups: Step-by-Step Guide

In this guide, we will walk you through the process of launching an **AWS EC2 instance** (using the free tier) and configuring **Security Groups** to secure your cloud instance. Security Groups are a crucial part of AWS security as they act as virtual firewalls, controlling inbound and outbound traffic to your EC2 instances.

## Step 1: Log into AWS Management Console

1. Go to the [AWS Management Console](https://aws.amazon.com/console/).
2. Sign in with your AWS account credentials.

---

## Step 2: Launch an EC2 Instance

1. In the AWS Console, search for **EC2** in the services search bar and select **EC2** under Compute.
2. Click **Launch Instance** to start the instance creation process.

### 2.1 Choose an Amazon Machine Image (AMI)
- Select an Amazon Machine Image (AMI) that suits your needs. For a basic EC2 instance, choose the **Amazon Linux 2 AMI** (free tier eligible).

### 2.2 Choose an Instance Type
- Select the **t2.micro** instance type (free tier eligible).
- Click **Next: Configure Instance Details**.

### 2.3 Configure Instance Details
- You can keep the default settings here. For this guide, leave them as is.
- Click **Next: Add Storage**.

### 2.4 Add Storage
- You can stick with the default storage settings (8 GB of general-purpose SSD storage).
- Click **Next: Add Tags**.

### 2.5 Add Tags
- Tags are useful for organizing your resources. You can add tags to your EC2 instance, but for now, you can skip this step.
- Click **Next: Configure Security Group**.

---

## Step 3: Create and Configure a Security Group

### 3.1 Define Security Group Rules
- **Security Groups** act as a virtual firewall for your EC2 instance. They control both inbound and outbound traffic. You'll need to define **Inbound** and **Outbound** rules.

#### 3.1.1 Inbound Rules
- These rules define which traffic is allowed into your EC2 instance.
    - **SSH (Port 22)**: Add a rule to allow SSH traffic for remote access to your EC2 instance. 
      - Type: **SSH**
      - Protocol: **TCP**
      - Port Range: **22**
      - Source: **My IP** (only allow access from your IP for security reasons).
    - **HTTP (Port 80)**: Add a rule to allow HTTP traffic for accessing websites hosted on the instance.
      - Type: **HTTP**
      - Protocol: **TCP**
      - Port Range: **80**
      - Source: **Anywhere** (0.0.0.0/0) if you want the instance to be publicly accessible.

#### 3.1.2 Outbound Rules
- By default, Security Groups allow all outbound traffic, meaning your EC2 instance can reach any external service. If you want to restrict outbound traffic, you can modify this, but for now, we'll leave it as is.

#### 3.1.3 Review and Create
- **Review your rules** and make sure they are correct.
- Click **Review and Launch**.
- A summary of your configuration will appear. Verify everything and click **Launch**.
  
---

## Step 4: Select a Key Pair for SSH Access

1. If you don’t have an existing key pair, choose **Create a new key pair**.
2. Name your key pair (e.g., `my-key-pair`).
3. Download the **.pem** file and keep it safe. This file is required for SSH access to your EC2 instance.

---

## Step 5: Access Your EC2 Instance

Once your EC2 instance is up and running:

1. Go to the **Instances** section in your EC2 dashboard.
2. Find your instance in the list and note its **Public IP** address.
3. Use the **SSH** client to connect to your instance using the key pair you downloaded earlier.

### 5.1 Connect via SSH
- Open a terminal and run the following command:
  ```bash
  chmod 400 my-key-pair.pem
  ssh -i "my-key-pair.pem" ec2-user@<Your_Public_IP>
