# ACE Cloud Explorer

ACE Cloud Explorer is an AWS-based cloud project designed to demonstrate a secure public/private network architecture and dynamic access to cloud service data stored in Amazon S3.

## Project Overview

The project uses AWS networking and compute services to host a web application inside a custom VPC.

The architecture includes:
- A custom VPC
- Public and private subnets
- EC2 instances
- A bastion host for secure access to the private instance
- Amazon S3 for storing application data
- IAM roles for secure access to S3 without hard-coded credentials

## Technologies Used

- AWS VPC
- Amazon EC2
- Amazon S3
- AWS IAM
- Linux
- Apache
- PHP
- HTML/CSS
- Git and GitHub

## Architecture

The application is deployed inside a custom AWS VPC.

A public EC2 instance is located in the public subnet and can communicate with the internet through an Internet Gateway. A private EC2 instance is isolated from direct internet access.

The public instance also acts as a bastion host, allowing secure SSH access to the private instance.

Application data is stored in a private Amazon S3 bucket. EC2 accesses the bucket using an IAM role attached through an instance profile, avoiding the need to store AWS access keys on the server.

## Architecture Diagram

The diagram below shows the AWS architecture used in ACE Cloud Explorer.

![ACE Cloud Explorer Architecture](architecture/architecture.png)

## How the Architecture Works

1. The user accesses the ACE Cloud Explorer web application through the public EC2 instance.
2. The public EC2 instance is hosted inside a public subnet connected to an Internet Gateway.
3. Application data is stored in a private Amazon S3 bucket.
4. The EC2 instance accesses S3 through an IAM role attached to the instance, so AWS access keys do not need to be stored in the application.
5. A private EC2 instance is placed inside the private subnet and cannot be accessed directly from the internet.
6. Administrative access to the private instance is performed through the public EC2 instance acting as a bastion host.

## Project Screenshots

### ACE Cloud Explorer Web Application

The application dynamically displays AWS cloud service information retrieved from Amazon S3.

![ACE Cloud Explorer Web Application](Screenshots/ace-home-page.jpg)

### Amazon S3 Data Source

Cloud service data is stored in a private S3 bucket and retrieved by the EC2 application using an IAM role.

![Amazon S3 Data](Screenshots/s3-services-data.jpg)

### Private EC2 Access

The private EC2 instance has no public IP address and is accessed through the public EC2 instance acting as a bastion host.

![Private EC2 Access](Screenshots/private-ec2-access.jpg)

## Challenges and Troubleshooting

### Accessing the Private EC2 Instance

One challenge during the project was securely accessing the EC2 instance inside the private subnet.

The private instance does not have a public IP address, so it cannot be accessed directly from the internet. The public EC2 instance was used as a bastion host to reach the private instance through its private IP address.

This helped demonstrate how private cloud resources can remain isolated from direct internet access while still allowing controlled administrative access.

### Accessing S3 Without Hard-Coded Credentials

The application needed permission to retrieve the `services.json` file from Amazon S3.

Instead of storing AWS access keys inside the application, an IAM role was attached to the EC2 instance through an instance profile. This allowed the application to access the required S3 object securely using temporary AWS credentials provided by the instance role.
