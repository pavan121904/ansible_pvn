# Automated Security Patching with Ansible

This Ansible playbook automates the process of updating packages, including security patches, and can reboot the server if necessary.

## Usage

1. Ensure Ansible is installed on your control machine.

2. Create an Ansible playbook file (e.g., `security_patching.yml`) and add the following tasks:

```yaml
- name: Update package cache
  apt:
    update_cache: yes

- name: Upgrade packages (security patches)
  apt:
    name: '*'
    state: latest
    update_cache: yes

- name: Reboot if needed after package upgrades
  command: shutdown -r now
  async: 1
  poll: 0

