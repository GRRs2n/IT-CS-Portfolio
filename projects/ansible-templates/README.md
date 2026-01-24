# Ansible Templates and Jinja2 for Web Configuration

## Overview
This project showcases how to use Ansible’s `template` module and Jinja2 templates to deploy dynamic web pages and configuration files across multiple hosts. Using Visual Studio Code’s remote SSH integration and SSH tunneling for secure access, we developed a custom template that personalizes each host’s landing page based on its facts (IP address, operating system, date/time, etc.).

## What I Did
- **Remote editing via VS Code:** Connected to the control node over SSH and used the VS Code remote editor to create and manage files.
- **SSH tunnelling:** Created a tunnel (`ssh -L`) to forward remote port 80 to the local machine so the web pages could be tested directly from VS Code.
- **Jinja2 template:** Wrote `index.html.j2` containing placeholders such as `{{ ansible_facts['default_ipv4']['address'] }}` and `{{ ansible_facts['distribution'] }}` to insert each host’s IP, OS, and timestamp.
- **Playbook and inventory:** Added new hosts to the Ansible inventory and created a playbook that:
  - Installs Apache/Nginx if not present.
  - Uses the `template` module to generate `/var/www/html/index.html` from the Jinja2 file.
  - Reloads the web server to apply changes.
- **Validation:** Ran the playbook with `ansible-playbook` and confirmed that each target host served a customized landing page with the correct details.

## Lessons Learned
- Jinja2 templates enable dynamic, reusable configuration files.
- Ansible facts provide host‑specific data without hard‑coding values.
- VS Code’s remote SSH extension streamlines development on remote hosts.
- SSH tunnelling is essential for securely previewing web content from internal networks.

## Next Steps
- Expand the template to configure additional services (e.g., Nginx vhosts, PHP settings).
- Move host variables into group_vars and use defaults to simplify the playbook.
- Explore version control for templates to track changes over time.
