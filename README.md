# AWS Secure Website Project

## Overview
This project sets up a secure AWS architecture using a Virtual Private Cloud (VPC) with public and private subnets. The setup ensures high availability, security, and scalability for hosting a website securely in a private subnet.

### Architecture Diagram
![image](https://github.com/user-attachments/assets/148927d8-46cc-4fc5-b685-5b5e72ad2f56)



### Components:
- **Public Subnets**: Contain NAT gateways for outbound internet access.
- **Private Subnets**: Host EC2 instances in an Auto Scaling group.
- **Application Load Balancer**: Routes traffic securely to private instances.
- **Route Tables**: Control traffic routing within subnets.
- **Auto Scaling Group**: Ensures scalability by automatically adjusting the number of EC2 instances.

## Deployment Steps

### Step 1: Create the VPC
1. Open **Amazon VPC Console**.
2. Click **Create VPC** and configure:
   - **Two Private Subnets**
   - **Two Public Subnets**
3. Create **Three Route Tables**:
   - **One for Public Subnets**
   - **Two for Private Subnets**
4. Configure Route Tables for Subnets.
5. Create and attach an **Internet Gateway** to the VPC.

### Step 2: Configure NAT Gateway
1. Create **NAT Gateway**.
2. Attach it to each **Private Subnet**.

### Step 3: Security Group Settings
1. Configure Security Groups for **Auto Scaling Group**.

### Step 4: Create Auto Scaling Group
1. Create a **Template** for Auto Scaling Group.
2. Configure scaling policies.

### Step 5: Create Bastion Host
1. Launch **Bastion Host** in the same VPC.
2. Assign a **public IP**.

### Step 6: SSH to Private EC2 Instances
1. Copy the **private key** to the Bastion Host:
   ```sh
   scp -i EC2_Instance.pem EC2_Instance.pem ec2-user@<Bastion_Host_IP>:/home/ec2-user
   ```
2. SSH into the Bastion Host:
   ```sh
   ssh -i EC2_Instance.pem ec2-user@<Bastion_Host_IP>
   ```
3. SSH into a private EC2 instance:
   ```sh
   ssh -i EC2_Instance.pem ec2-user@<Private_Instance_IP>
   ```

### Step 7: Setup Website in Private EC2 Instance
1. Deploy your website on the **private instance**.

### Step 8: Configure Load Balancer
1. Create a **Load Balancer**.
2. Create a **Target Group** including private EC2 instances.
3. Configure **Security Groups**:
   - **Load Balancer**: Ports **80, 8000**.
   - **Auto Scaling**: Ports **22, 8000**.

### Step 9: Testing Load Balancer
- When both EC2 servers are **Live**, traffic is distributed.
- When one server is **Down**, traffic shifts to the active server.

## Conclusion
This project successfully deploys a secure website using AWS public-private subnet architecture, ensuring availability and security.

### Connect with Me
[LinkedIn](https://www.linkedin.com/in/ajitpal2182/)

