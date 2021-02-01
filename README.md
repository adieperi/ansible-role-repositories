# ansible-role-repositories
Ansible role to manage package repositories

## How to install
### requirements.yml
**Put the file in your roles directory**
```yaml
---
- src: https://github.com/adieperi/ansible-role-repositories.git
  scm: git
  version: master
  name: ansible-role-repositories
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
    - name: Role repositories
      include_role:
        name: ansible-role-repositories
      vars:
        addBaseRepositories: true
        repositories:
          # First option when is not PPA
          add:
            url: "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main"

          # Second option when is a PPA
          add:
            url: "ppa:ansible/ansible"
            # Optional
            codename: trusty

          # First option when is not PPA
          remove:
            url: "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main"

          # Second option when is a PPA
          remove:
            url: "ppa:ansible/ansible"
            codename: trusty
```
