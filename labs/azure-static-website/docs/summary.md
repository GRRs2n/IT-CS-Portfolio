# Detailed Summary: Hosting a Static Website on Azure Blob Storage

## Objective
This lab guided the process of enabling static website hosting on an existing Azure StorageV2 account, deploying web content via a provided script, and verifying the resulting website.

## Steps Performed
- Verified the Azure CLI environment and active subscription.
- Identified the target resource group and StorageV2 account for static website hosting.
- Downloaded the lab files containing a Bash script and website content (HTML and assets).
- Edited variables in the script to specify the resource group and storage account names.
- Made the script executable and ran it. The script:
  - Created a storage container and configured the storage account for static website hosting.
  - Uploaded the website files to the `$web` container.
  - Output the static website endpoint URL upon completion.
- Retrieved and noted the website endpoint URL from the script output (e.g., `https://<account>.z13.web.core.windows.net`).
- Verified the site by navigating to the endpoint in a browser and viewing the deployed pages.
- Observed the difference between authentication contexts: Azure CLI login uses Azure AD identities, while storage access keys or SAS tokens are required to upload content via the Azure Storage API.

## Key Learnings
- Azure StorageV2 accounts support static website hosting, which must be explicitly enabled for the `$web` container.
- Automation scripts streamline enabling features and deploying content; variables should be customized for the user's environment.
- The CLI authentication (via `az login`) is distinct from the storage account credentials used by the website script.
- After enabling static website hosting, the service provides a unique endpoint for hosting web content that can be shared publicly.
