# AWS CLI Setup and Basic S3 Operations

## Overview
This lab documents the installation and initial configuration of the AWS Command Line Interface (CLI) and a simple exercise using a Bash script to create and interact with an S3 bucket. Using CLI tools instead of the console builds automation skills and highlights how credentials and permissions enable programmatic access.

## Steps Performed
- Installed the AWS CLI on a Mac and verified that the `aws` binary was in the system PATH with `which aws` and `aws --version`.
- In the AWS console, created an administrative IAM user and enabled both console and programmatic access.
- Generated an access key and secret key, then configured the CLI with `aws configure` by specifying the credentials and default region.
- Executed a provided shell script to create a unique S3 bucket, count existing objects, upload a test file, and confirm the final object count.

## What I Learned
- The AWS CLI provides a command-driven interface to AWS services, using Access Key ID and Secret Access Key credentials configured through IAM.
- S3 buckets serve as globally unique containers for objects; CLI commands can list, create, and manage these buckets.
- Automating bucket creation and file uploads in a script ensures consistency and reduces manual steps.
