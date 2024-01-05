# ec2-instance-basics
A beginner's guide to AWS EC2. Learn to launch instances, connect via SSH, create key pairs, configure security groups, and run basic bash scripts. Ideal for AWS newcomers.

---

# EC2 Instance Setup README

## Table of Contents

1. [Launching an EC2 Instance on AWS](#1-launching-an-ec2-instance-on-aws)
2. [Connecting to EC2 Instance using SSH](#2-connecting-to-ec2-instance-using-ssh)
3. [Creating a Key Pair](#3-creating-a-key-pair)
4. [Creating a Security Group](#4-creating-a-security-group)
5. [Associating Key Pair and Security Group with EC2 Instance](#5-associating-key-pair-and-security-group-with-ec2-instance)
6. [Connecting to EC2 Instance Using SSH](#6-connecting-to-ec2-instance-using-ssh)
7. [Creating and Running a Bash Script on EC2 Instance](#7-creating-and-running-a-bash-script-on-ec2-instance)

---

## 1. Launching an EC2 Instance on AWS

### Prerequisites:

- AWS account with necessary permissions.
- Access to the AWS Management Console.

### Steps:

1. Sign in to the AWS Management Console.

2. Navigate to EC2 in the "Services" tab.

3. Launch a new instance:
   - Choose an Amazon Machine Image (AMI).
   - Select an instance type.
   - Configure instance details.
   - Add storage.
   - Add tags (optional).
   - Configure security group.
   - Review and launch.

4. Choose or create a key pair:
   - Select an existing key pair or create a new one.
   - Download the private key file (.pem).

5. View instances and monitor the status of your launched instance.

---

## 2. Connecting to EC2 Instance using SSH

### Prerequisites:

- Private key file (.pem) associated with the chosen key pair.

### Steps:

1. Open a terminal or command prompt.

2. Navigate to the directory where the private key file is located.

3. Change the permissions of the private key file:
   ```bash
   chmod 400 your-key-pair.pem
   ```

4. Connect to the EC2 instance using SSH:
   ```bash
   ssh -i "your-key-pair.pem" ec2-user@your-instance-ip
   ```

---

## 3. Creating a Key Pair

### Steps:

1. Navigate to EC2 in the AWS Management Console.

2. Under "Network & Security," click on "Key Pairs."

3. Create a new key pair:
   - Key pair name: `ec2key`
   - Key pair type: `RSA`
   - Private key file format: `.pem`

4. Download the private key file (.pem).

---

## 4. Creating a Security Group

### Steps:

1. Navigate to EC2 in the AWS Management Console.

2. Under "Network & Security," click on "Security Groups."

3. Create a new security group:
   - Security group name: `MySecurityGroup`
   - Inbound rules: Allow SSH (port 22) from anywhere.
   - Outbound rules: Allow all traffic.

4. Review and create the security group.

---

## 5. Associating Key Pair and Security Group with EC2 Instance

### Steps:

1. Launch a new EC2 instance following the steps in "Launching an EC2 Instance on AWS."

2. In the launch wizard:
   - Choose the existing key pair (`ec2key`).
   - Select the created security group (`MySecurityGroup`).

3. Complete the launch wizard and launch the instance.

---

## 6. Connecting to EC2 Instance Using SSH

### Prerequisites:

- Private key file (`ec2key.pem`).
- Public IP address or DNS name of the EC2 instance.

### Steps:

1. Open a terminal.

2. Connect to the EC2 instance using SSH:
   ```bash
   ssh -i "ec2key.pem" ec2-user@your-instance-ip
   ```

---

## 7. Creating and Running a Bash Script on EC2 Instance

### Steps:

1. Connect to your EC2 instance using SSH.

2. Create a new bash script:
   ```bash
   nano ec2script.sh
   ```

3. Add script content:
   ```bash
   #!/bin/bash

  echo "Hello! What is your name?"
  read name

  echo "Nice to meet you, $name!"

   ```

4. Save and exit the text editor.

5. Make the script executable:
   ```bash
   chmod +x ec2script.sh
   ```

6. Run the script:
   ```bash
   ./ec2script.sh
   ```

---
