# AWS Elastic File System (EFS) Setup – Detailed Summary

## Activities Performed

- Logged into the AWS Management Console and created an Amazon Elastic File System (EFS) with a lifecycle policy that transitions infrequently accessed files to a lower-cost storage class after seven days.
- Provisioned a t2.micro EC2 instance using the Amazon Linux 2023 AMI and generated an SSH key pair to enable secure connection.
- Connected to the instance via SSH and verified the operating system using `uname -a`.
- Installed the `amazon-efs-utils` package, resolving repository timeouts by cleaning and rebuilding the package cache with `dnf clean all` and `dnf makecache`.
- Configured a mount point on the EC2 instance and attempted to mount the EFS file system. Initial failures were due to DNS resolution and mount target availability; after verifying that mount targets were available in the same VPC and availability zone as the instance, the mount succeeded.
- Validated the mount using `df -m` and tested read/write functionality by creating a file in the mounted directory.

## Key Learnings

- Amazon EFS provides a scalable, shared file system that can be mounted simultaneously by multiple EC2 instances; lifecycle policies help reduce storage costs.
- Successful mounting requires the EC2 instance and EFS mount targets to reside in the same VPC and availability zone.
- Troubleshooting package installation and networking issues involves using package manager commands and understanding AWS networking components.
- The `amazon-efs-utils` package simplifies mounting by handling NFS settings and encryption options.
- Verifying mounts and performing simple file operations confirms that the shared storage is configured correctly.
