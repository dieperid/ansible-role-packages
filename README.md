# ansible-role-packages
Ansible role for install a list of packages on a linux machine

## How to install
### requirements.yml
**Put the file in your roles directory**
```yaml
---
- src: https://github.com/adieperi/ansible-role-packages
  scm: git
  version: master
  name: ansible-role-packages
```
### Download the role
```Shell
ansible-galaxy install -f -r ./roles/requirements.yml --roles-path=./roles
```

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
          - kubelet

        unholdExtraPackages:
          - kubelet

        # first option (Update all packages on the system)
        updateSystemPackages: all
        
        # second option (Update selected packages on the system)
        updateSystemPackages:
          - kubelet
        
        # third option (Same as the second option but with version indication)
        updateSystemPackages:
          - kubelet=1.20.1-00
```
