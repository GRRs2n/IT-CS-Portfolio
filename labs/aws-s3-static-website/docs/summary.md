# AWS S3 Static Website – Detailed Summary

## Activities Performed

- Verified AWS CLI installation and authentication by running `which aws`, `aws --version`, and `aws s3 ls` to list existing buckets.
- Created a working directory and downloaded the necessary website files (HTML, CSS, JavaScript) and bucket policy JSON, removing any `.txt` extensions.
- Modified the bucket policy to allow public read access and made the deployment script executable using `chmod u+x`.
- Executed the provided script with a unique bucket name to create the S3 bucket, apply the bucket policy, enable static website hosting, and upload website content.
- Accessed the website via the S3 static website endpoint and confirmed that the HTML, CSS, and JavaScript rendered correctly, including dynamic weather information.

## Key Learnings

- Amazon S3 can host static websites by serving files directly, eliminating the need for a traditional web server; the `index.html` file acts as the entry point.
- Automating deployment with Bash scripts simplifies repetitive CLI commands and reduces manual configuration errors.
- Proper bucket policies are critical for public website hosting; understanding JSON structure and IAM principals is essential.
- Testing both through AWS CLI and browser ensures that objects are uploaded and permissions are correctly applied.
- This exercise reinforced the concepts of static content hosting, automation, and access control within AWS.
