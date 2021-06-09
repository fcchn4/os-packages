# Details

This ansible poroject is for automatic install on post-installation for Fedora Operating System.

The project have three playbooks:

- fedora-base.yml
- fedora-desktop.yml
- fedora-security.yml

## Versions

- Ansible: 2.9
- Fedora: 34
- XFCE: 4.16.0

## Commands

For **fedora-base.yml**:

```bash
$ ansible-playbook fedora-base.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```

For **fedora-desktop.yml**:

```bash
$ ansible-playbook fedora-desktop.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```

For **fedora-security.yml**:

```bash
$ ansible-playbook fedora-security.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```
