rustdesk_server_container_setup
=========

Ansible role for deploying the rustdesk server rootless podman containers.

Tested on:

- AlmaLinux 10
- Debian 12

Requirements
------------

Docker or Podman needs to be preinstalled.

Role Variables
--------------

    - "{{ rustdesk_server_container_setup_folder }}/id_ed25519"
    - "{{ rustdesk_server_container_setup_folder }}/id_ed25519.pub"

When you run the role first time, a private key and a public key will be generated if the key files don't already exist.
If the files already exist, they won't be recreated. 
If you want to create a new keypair, delete the key files and run the role.
If you want to migrate the setup to another system and keep the same keys, you can just pre-create the key files so they would be used right away during the deployment.

Dependencies
------------

Docker or Podman

Example Playbook
----------------

```ansible
---
- name: Deploy RustDesk server and configure firewall
  hosts: all
  gather_facts: true
  become: false

  roles:
    - rustdesk_server_container_setup
...
```

License
-------

MIT
