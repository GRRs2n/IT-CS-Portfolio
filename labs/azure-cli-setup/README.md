# Installing and Using the Azure CLI

## Overview
This lab documents the installation of the Azure Command Line Interface (CLI), authenticating to Azure, and verifying access to storage resources. The Azure CLI is a cross‑platform tool for managing Azure resources and scripting deployments.

## Steps Performed
- Installed the Azure CLI on macOS using a package manager and verified the installation by running `az --version`.
- Authenticated to Azure with `az login`, which launched a browser to complete the login process using institutional credentials.
- Listed available subscriptions and selected the appropriate one for lab work.
- Used `az storage account list` to enumerate storage accounts associated with the subscription.
- Retrieved a connection string for a storage account with `az storage account show-connection-string` to verify permissions.

## What I Learned
- The Azure CLI simplifies resource management and can be installed locally to interact with Azure without using the portal.
- Authentication via `az login` integrates with Azure Active Directory and reveals available subscriptions.
- Command-line tools are indispensable for automating deployments, scripting resource changes, and verifying configurations.
