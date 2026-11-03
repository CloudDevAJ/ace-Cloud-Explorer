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
