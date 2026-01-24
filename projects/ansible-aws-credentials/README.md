# Ansible AWS Credentials Setup

## Overview
This project summarizes a lab on preparing Ansible to manage AWS resources securely. It involves creating IAM identities, configuring environment variables, and verifying connectivity using Ansible's AWS modules.

## What I Did
- Updated the control node and ensured Python, Ansible, and the AWS collections were installed.
- In AWS IAM, created a group with policies for EC2, ECR, ECS, and S3, then created a user and added it to the group.
- Generated access keys for the user and saved them locally.
- Wrote a shell script (`awsAccessKeys.sh`) that exports `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` and used `source` to load the variables.
- Verified that the environment variables were set correctly using `env | grep AWS`.
- Tested Ansible's connection to AWS by running the `amazon.aws.aws_s3_bucket_info` module to list accessible S3 buckets【595590462850829†L8-L45】.
- Troubleshot issues due to typos in variable names or incorrectly sourced scripts until the module returned results.

## Lessons Learned
- Using IAM groups with attached policies simplifies permission management for multiple users.
- Exporting credentials as environment variables via a script reduces the risk of accidentally committing them to version control.
- Accurate variable names and proper sourcing (`source ./awsAccessKeys.sh`) are critical; typos prevent Ansible from authenticating【595590462850829†L8-L45】.
- Ansible’s AWS modules rely on the `amazon.aws` collection; verifying the collection installation and correct region configuration is essential.

## Next Steps
- Store AWS credentials more securely using AWS CLI profiles or AWS SSO instead of plain environment variables.
- Automate IAM user and policy creation via Terraform or CloudFormation.
- Explore additional Ansible modules such as `amazon.aws.ec2_instance` and `amazon.aws.s3` to provision and manage resources.
