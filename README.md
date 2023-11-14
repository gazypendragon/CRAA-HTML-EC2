# CRAA-HTML-EC2
This is a Repository for CRAA'S HTML Web Files to create Wep Apps on ec2 instances on Default vpc

# EC2 Instance Launch Script

This script automates the process of launching an EC2 instance on AWS and sets up a basic web server using Apache HTTP Server.

## Prerequisites

- AWS account with necessary permissions to create and manage EC2 instances.
- An IAM user or role with appropriate permissions and configured AWS CLI.
- A running Amazon EC2 instance with Amazon Linux 2 (or compatible) as the base image.

## Usage

1. Connect to your EC2 instance using SSH or other remote access methods.
2. Run the following commands in the terminal:

```bash
#!/bin/bash
sudo su
yum update -y
yum install -y httpd
yum install git -y
cd /var/www/html
git clone https://github.com/gazypendragon/CRAA-HTML-EC2.git
cd CRAA-HTML-EC2/
cp -r mole-main/* /var/www/html
rm -rf mole-main
systemctl enable httpd
systemctl start httpd
```

The script will update the system packages, install the Apache web server and Git, clone the contents of the specified GitHub repository, and deploy the web application to the `/var/www/html` directory.

## Important Note







## Hosting a Static Website on AWS

### Overview

This project demonstrates the deployment of a static HTML web app on AWS, utilizing various AWS services and resources to achieve scalability, high availability, and fault tolerance.

### Architecture

![Project Architecture Diagram](link_to_diagram)

### AWS Resources Utilized

1. **Virtual Private Cloud (VPC):**
   - Established a VPC with private and public subnets spanning two availability zones.

2. **Internet Gateway:**
   - Implemented an internet gateway to facilitate traffic between instances in the VPC and the internet.

3. **Security Groups:**
   - Employed security groups as firewalls to regulate inbound and outbound traffic.

4. **Availability Zones:**
   - Deployed resources across two availability zones for increased availability and fault tolerance.

5. **Public Subnet Resources:**
   - Placed NAT gateway, Bastion host, and Application Load Balancer (ALB) in public subnets.

6. **EC2 Instance Connect Endpoint:**
   - Leveraged the EC2 Instance Connect endpoint for secure SSH access to resources in both public and private subnets.

7. **Web Server and Database Placement:**
   - Deployed web servers and database servers in the public subnet for enhanced security.

8. **NAT Gateway for Internet Access:**
   - Enabled instances in private app and data subnets to access the internet through a NAT gateway.

9. **EC2 Instances for Website Hosting:**
   - Hosted the static website on EC2 instances.

10. **Application Load Balancer (ALB):**
    - Implemented an ALB to evenly distribute web traffic across an auto-scaling group of EC2 instances in multiple availability zones.

11. **Auto-Scaling Group:**
    - Utilized an auto-scaling group to dynamically create EC2 instances, ensuring high availability, scalability, fault tolerance, and elasticity.

12. **Route 53:**
    - Registered a domain name and created a record set using Route 53 for DNS management.

13. **GitHub:**
    - Utilized GitHub to store web files and enable version control.

14. **AMI Creation:**
    - Utilized the EC2 instance to create an Amazon Machine Image (AMI) for future instance launches.

### Deployment Script

The following script was used to deploy the web app on an EC2 instance:

```bash
#!/bin/bash

# Update and install necessary packages
sudo su
yum update -y
yum install -y httpd
sudo yum install git -y

# Clone the web app repository
cd /var/www/html
git clone <repository_url>

# Copy web app files
cd CRAA-HTML-EC2/
cp -r mole-main/* /var/www/html/
rm -rf mole-main

# Enable and start the Apache web server
systemctl enable httpd
systemctl start httpd
```

### Instructions for Use

1. **Clone the Repository:**
   - Clone this GitHub repository to your local machine.

2. **Configure AWS Resources:**
   - Use the provided architecture diagram and the AWS Management Console to set up the necessary resources.

3. **Update Deployment Script:**
   - Modify the script to include the correct repository URL.

4. **Run the Deployment Script:**
   - Execute the script on your EC2 instance to deploy the web app.

5. **Access the Website:**
   - Once deployed, access the static website using the public DNS or IP address of the load balancer.



### Acknowledgments


- Ensure that your EC2 instance has the necessary security group rules to allow incoming traffic on port 80 (HTTP) so that your web server is accessible from the internet.
- For security reasons, avoid running the script with root privileges unless necessary. It's recommended to create a limited privilege user and execute the script using that user.

