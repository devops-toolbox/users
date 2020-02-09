Role Name
=========

users

[![Build Status](https://travis-ci.org/cmihai-ansible/users.svg?branch=master)](https://travis-ci.org/cmihai-ansible/users)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.users](https://galaxy.ansible.com/devopstoolbox.users)

```bash
ansible-galaxy install devopstoolbox.users
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.

Role Variables
--------------

```yaml
users_groups:
  - wheel

users_username:
  - name: devops
    sudo: true
    shell: /usr/bin/bash
    groups: wheel
    # ssh_key: "{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"
    comment: 'Created by ansible'
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install users on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: users is configured
      import_role:
        name: devopstoolbox.users
      vars:
        users_groups:
          - wheel

        users_username:
          - name: devops
            sudo: true
            shell: /usr/bin/bash
            groups: wheel
            # ssh_key: "{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"
            comment: 'Created by ansible'
      tags: users
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
