# Deploying a Static Website on Amazon S3

## Overview
This lab demonstrates how to use the AWS CLI and a Bash script to provision and configure a static website hosted on Amazon S3. Serving static content directly from S3 eliminates the need for a web server and is suitable for simple sites without backend logic.

## Steps Performed
- Confirmed that the AWS CLI was installed and authenticated by running `which aws`, `aws --version` and `aws s3 ls`.
- Created a working directory and downloaded provided website files (HTML, CSS, JavaScript, and a bucket policy JSON). Removed any extraneous file extensions.
- Made the deployment script executable (`chmod u+x`) and ran it with a unique bucket name. The script created the bucket, applied the policy, enabled static website hosting, and uploaded the site files.
- Retrieved the S3 static website endpoint and verified that the site loaded correctly in the browser with all assets rendered.

## What I Learned
- S3 static website hosting serves files directly to browsers, using `index.html` as the landing page and an optional error page.
- Automation scripts can chain multiple CLI commands to create buckets, apply bucket policies for public access, and deploy content.
- Configuring bucket policies correctly is essential to allow public read access while securing other resources.
