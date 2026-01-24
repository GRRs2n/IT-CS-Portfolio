# Deploy Docker Image to AWS ECR

## Overview
This project demonstrates pushing a container image to Amazon Elastic Container Registry (ECR), using AWS CLI and Docker to authenticate, tag, and upload an image, and utilizing ECR's vulnerability scanning feature.

## What I Did
- Loaded AWS credentials into the shell environment using an `awsAccessKeys.sh` script, ensuring the `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, and region variables were exported.
- Verified that Docker and the AWS CLI were installed and that the local image (`cplhello`) existed.
- Created a private ECR repository using `aws ecr create-repository`.
- Retrieved a temporary login token with `aws ecr get-login-password` and authenticated to ECR using `docker login` with the full registry URI.
- Tagged the local image with the ECR repository URI, e.g., `docker tag cplhello $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/cplhello`.
- Pushed the tagged image to ECR using `docker push`.
- Verified the image was stored in ECR via the AWS Console and initiated a vulnerability scan.
- Reviewed the scan findings, noting any high or critical vulnerabilities.

## Lessons Learned
- Amazon ECR provides secure, private storage integrated with AWS IAM; pushing images requires proper credentials and region configuration.
- Authentication to ECR uses a temporary password obtained via `aws ecr get-login-password` rather than static credentials.
- Tagging images with the full repository URI is essential; omitting it causes push failures.
- Running vulnerability scans on container images before deployment helps identify known CVEs early.
- Region and account settings must be consistent across AWS CLI and Docker commands.

## Next Steps
- Automate the login and push steps within a CI/CD pipeline to streamline deployments.
- Configure lifecycle policies to automatically expire old images.
- Integrate image scanning results into deployment gates or monitoring dashboards.
