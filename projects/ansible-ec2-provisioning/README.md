# Ansible EC2 Provisioning

## Overview
This project demonstrates how to use Ansible to provision and manage an EC2 instance on AWS. It shows how infrastructure as code simplifies creating and terminating instances.

## What I Did
- Generated a key pair for SSH access (`demo-key.pem`) and ensured it was available to Ansible.
- Wrote a playbook `CPL_demo_ec2.yml` using the `amazon.aws.ec2_instance` module to launch an EC2 instance with a specified AMI, instance type, subnet, security group, and tags.
- Executed the playbook with `ansible-playbook CPL_demo_ec2.yml` to create the instance.
- Verified in the AWS console that the instance was running and accessible.
- After validation, updated the playbook to set the `state` to `absent` and ran it again to terminate the instance, demonstrating idempotent infrastructure management【957861347912074†L7-L34】.

## Lessons Learned
- Ansible's cloud modules, like `amazon.aws.ec2_instance`, make it easy to provision AWS resources declaratively.
- Always specify the region and AMI ID correctly; mismatches cause playbook failures.
- Using key pairs enables secure SSH access without storing passwords.
- Idempotent playbooks allow the same code to create or destroy resources simply by changing parameters【957861347912074†L7-L34】.

## Next Steps
- Extend the playbook to configure the instance after launch (install packages, deploy apps).
- Use variables and inventory to parameterize instance types and counts.
- Integrate with AWS VPC and security group modules to build complete environments.
