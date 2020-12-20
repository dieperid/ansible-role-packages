# ansible-role-packages
Ansible role for install a list of packages on a linux machine

## Exemple Playbook
```yaml
---
- hosts: all
  tasks:
    - name: Install base packages
      include_role:
        name: ansible-role-packages
      vars:
        installExtraPackages:
          - nmon
        removeExtraPackages:
          - htop
        holdExtraPackages:
          - nmon
```
