# Ansible Role: Automated WordPress Deployment

## Overview 
This project demonstrates how to package a WordPress deployment into a reusable Ansible role. The role installs a complete LAMP stack (Apache, MySQL/MariaDB and PHP), configures the database and WordPress, applies a templated `wp-config.php`, and ensures proper permissions and idempotent operations.

## What I Did

- **Initialize the role skeleton:** Used `ansible-galaxy init wordpress` to create the directory structure (`tasks`, `handlers`, `templates`, `vars`, etc.).
- **Tasks:** Added tasks to:
  - Install Apache, PHP and MySQL/MariaDB along with required modules.
  - Create a MySQL database and user for WordPress.
  - Download and extract the latest WordPress archive.
  - Copy a templated `wp-config.php` using the `template` module with variables for database name, user and password.
  - Set file ownership to `www-data` and adjust SELinux contexts if necessary.
- **Handlers:** Added a handler to restart Apache whenever configuration files change.
- **Variables:** Defined defaults in `defaults/main.yml` to allow easy customisation of database credentials and site settings.
- **Playbook:** Wrote a simple playbook that applies the `wordpress` role to the target hosts.
- **Remote editing with VS Code:** Used VS Code Remote SSH to edit role files on the control node and push changes to the repository via Git.
- **Verification:** Ran the playbook and verified the WordPress site was reachable via HTTP and presented the initial setup page.

## Lessons Learned

- Roles provide a structured way to organise Ansible code for reusability and clarity.
- The `template` module and Jinja2 templating allow injecting variables into configuration files cleanly.
- Idempotent tasks ensure repeated runs do not produce unwanted side effects.
- Using handlers keeps services restarted only when necessary.

## Next Steps

- Enhance the role to support SSL/TLS termination and optional Nginx front‑end.
- Store sensitive credentials using Ansible Vault and prompt the user at runtime.
- Publish the role to Ansible Galaxy as part of a personal collection and use it in larger infrastructure deployments.
