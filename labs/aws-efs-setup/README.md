# Creating and Mounting an Amazon Elastic File System

## Overview
This lab covers the process of provisioning an Amazon Elastic File System (EFS), launching an Amazon EC2 instance, installing necessary utilities, and mounting the file system. The exercise emphasizes troubleshooting common issues and understanding how EFS integrates with EC2.

## Steps Performed
- Created a new EFS file system in the AWS console and configured a lifecycle policy to transition files to an infrequent access tier after a set period. Verified settings such as performance and throughput modes.
- Launched a small EC2 instance using the Amazon Linux 2023 AMI, generated an SSH key pair, and connected to the instance.
- Installed the `amazon-efs-utils` package; resolved package repository errors by cleaning and rebuilding the package cache.
- Created a mount directory and mounted the EFS file system to the instance, troubleshooting DNS and mount target availability issues by ensuring the file system and instance shared the same VPC and availability zone.
- Confirmed the mount with `df -m` and tested read/write functionality by creating files in the mounted directory.

## What I Learned
- Amazon EFS provides scalable, shared storage accessible from multiple EC2 instances over the NFS protocol.
- Lifecycle policies help manage storage costs by automatically moving data to lower-cost storage tiers.
- Proper networking configuration (VPC, security groups, mount targets) is critical for successful EFS mounts.
- Troubleshooting skills are needed to resolve repository issues, DNS resolution problems, and mounting errors.
