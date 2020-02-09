Role Name
=========

linux-packages: Linux-packages

[![Build Status](https://travis-ci.org/cmihai-ansible/linux-packages.svg?branch=master)](https://travis-ci.org/cmihai-ansible/linux-packages)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.linux-packages](https://galaxy.ansible.com/devopstoolbox.linux-packages)

```bash
ansible-galaxy install devopstoolbox.linux-packages
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
linux-packages_packages_state: present
linux-packages_remove_packages: true
linux-packages_enable_service: true
linux-packages_enable_selinux: true
linux-packages_copy_templates: true
linux-packages_firewall_configure: true
linux-packages_firewall_rules:
  - service: ssh
  - port: 3389
linux-packages_users:
  - user: devops
    group: docker
linux-packages_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install linux-packages on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: linux-packages is configured
      import_role:
        name: devopstoolbox.linux-packages
      vars:
        linux-packages_packages_state: present
        linux-packages_remove_packages: true
        linux-packages_enable_service: true
        linux-packages_enable_selinux: true
        linux-packages_copy_templates: true
        linux-packages_firewall_configure: true
        linux-packages_firewall_rules:
          - service: ssh
          - port: 3389
        linux-packages_users:
          - user: devops
            group: docker
        linux-packages_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: linux-packages
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
