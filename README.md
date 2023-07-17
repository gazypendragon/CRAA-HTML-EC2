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

- Ensure that your EC2 instance has the necessary security group rules to allow incoming traffic on port 80 (HTTP) so that your web server is accessible from the internet.
- For security reasons, avoid running the script with root privileges unless necessary. It's recommended to create a limited privilege user and execute the script using that user.

