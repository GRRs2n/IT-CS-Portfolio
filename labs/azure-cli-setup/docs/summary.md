# Detailed Summary: Installing and Using the Azure CLI

## Objective
This lab documents the installation of the Azure Command Line Interface (CLI) on a macOS system, authentication to Azure, and enumeration of storage resources and connection strings using CLI commands.

## Steps Performed
- Installed the Azure CLI on macOS using Homebrew.
- Verified installation with `az --version`.
- Logged in to Azure using `az login`, launching a browser to authenticate with institutional credentials and confirm available subscriptions.
- Enumerated available subscriptions and selected the appropriate subscription for lab work using `az account list` and `az account set`.
- Listed existing storage accounts using `az storage account list`.
- Retrieved connection strings for a storage account with `az storage account show-connection-string -n <account-name> -g <resource-group>`.
- Confirmed access by connecting to the storage account using the connection string.

## Key Learnings
- The Azure CLI is a cross-platform tool that simplifies management of Azure resources via command-line automation.
- Verifying environment and subscription context is critical to avoid accidental changes in wrong subscriptions.
- CLI commands allow rapid enumeration of resources (e.g., storage accounts) and retrieval of secrets (e.g., connection strings) needed for scripting and automation.
- Scripts can be combined with the CLI for repeatable deployments and management tasks, improving efficiency and consistency.
