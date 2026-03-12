# AWS Hands-on: Mounting Amazon EFS on EC2 Instances

This project demonstrates the process of creating an Amazon Elastic File System (EFS) and mounting it onto an Amazon EC2 instance running Amazon Linux 2023. This setup allows for scalable, shared storage that can be accessed by multiple instances simultaneously.

## 🚀 Project Overview
The goal of this lab was to establish a persistent storage solution that scales automatically. By mounting EFS to an EC2 instance, I gained experience in VPC security configuration, Linux package management, and file system administration.

## 🛠 Tech Stack
* **Cloud Provider:** AWS
* **Services:** Amazon EC2, Amazon EFS, VPC (Security Groups)
* **Tools:** AWS CloudShell, `amazon-efs-utils`
* **Operating System:** Amazon Linux 2023

## 📝 Key Steps Taken

### 1. EFS File System Creation
Created an EFS file system named `Internfile` in the `ap-southeast-2` (Sydney) region, ensuring encryption at rest was enabled.

### 2. Security Group Configuration
Modified the default VPC Security Group to allow inbound traffic on **Port 2049 (NFS)**. This step is critical to allow the EC2 instance to communicate with the EFS mount targets.

### 3. Mounting EFS to EC2
Using AWS CloudShell, I performed the following:
* Installed the EFS mount helper: 
    ```bash
    sudo dnf install -y amazon-efs-utils
    ```
* Created a mount directory:
    ```bash
    mkdir efs
    ```
* Mounted the file system using the EFS ID:
    ```bash
    sudo mount -t efs -o tls fs-0695211af6e176bad:/ efs
    ```

### 4. Verification
Verified the successful mount by running the `df -h` command, which showed the EFS file system attached to the `/home/ec2-user/efs` directory.

## 📊 Results
* **File System ID:** `fs-0695211af6e176bad`
* **Region:** ap-southeast-2
* **Outcome:** Successful persistent storage attachment with auto-scaling capabilities.


*Created as part of my continuous learning journey in AWS Cloud Infrastructure.*
