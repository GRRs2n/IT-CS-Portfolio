# Ansible VM Setup and Basic Usage

## Overview
This project summarizes two labs on setting up a control node (Fedora) and a target node (Ubuntu), installing and configuring Ansible, and verifying remote management. It shows how to prepare VMs, install required tools, configure SSH keys, and run Ansible ad‑hoc commands.

## What I Did
- Created a Fedora VM for the control node and an Ubuntu VM for the managed host.
- Installed and enabled OpenSSH on both VMs, along with Python 3, pip, Ansible, and the boto/boto3 library for AWS.
- Verified Ansible installation with `ansible --version` and performed system updates using `dnf update` on Fedora and `apt update` on Ubuntu【854318776833894†L7-L36】.
- Generated an SSH key on the control node and copied it to the managed node using `ssh-copy-id`, enabling passwordless authentication.
- Added the managed node to the Ansible inventory file (usually `/etc/ansible/hosts`) and tested connectivity with `ansible all -m ping`.
- Ran ad‑hoc commands like `ansible all -a "ps aux"`, `ansible all -a "free -h"`, and `ansible all -a "date"` to retrieve process, memory, and time information across hosts【787575250095707†L7-L68】.

## Lessons Learned
- The Fedora and Ubuntu distributions use different package managers (`dnf` vs `apt`) and service names; verifying dependencies like Python, Jinja2, and libyaml is critical for Ansible【854318776833894†L7-L36】.
- Key‑based SSH authentication improves security and convenience over password‑based logins【787575250095707†L7-L68】.
- The inventory file is central to Ansible; ad‑hoc commands provide a quick way to run tasks without writing playbooks【787575250095707†L7-L68】.
- Regular system updates and service verification ensure that Ansible runs smoothly.

## Next Steps
- Write simple playbooks to automate repeated tasks instead of using ad‑hoc commands.
- Experiment with roles, variables, and handlers to manage larger environments.
- Integrate Ansible with cloud platforms (e.g., AWS modules) to provision and configure resources.
