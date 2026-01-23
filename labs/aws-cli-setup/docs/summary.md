# AWS CLI Setup and Basic S3 Operations – Detailed Summary

## Activities Performed

- Verified the AWS CLI installation on macOS using `which aws` and `aws --version`, ensuring version 2+.
- Logged in to the AWS console, created an IAM administrator user with console and programmatic access, and generated an access key pair for CLI authentication.
- Configured the AWS CLI via `aws configure`, specifying access keys and default region.
- Executed a provided shell script to create a unique S3 bucket, verify bucket existence, and upload a test file.

## Key Learnings

- The AWS CLI provides a command-driven method to interact with AWS services, complementing the web console.
- IAM users and access keys enable secure programmatic access; credentials must be protected.
- S3 organizes data into buckets with unique names; CLI commands such as `aws s3 ls` list buckets and objects.
- Automating bucket operations via scripts ensures consistency and reduces manual error.
- Understanding CLI configuration and credentials is foundational for future automation and infrastructure management.
