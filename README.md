# ansible-role-etherpad


[![Build Status](https://github.com/systemli/ansible-role-etherpad/workflows/Integration/badge.svg?branch=master)](https://github.com/systemli/ansible-role-etherpad/actions?query=workflow%3AIntegration)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-etherpad-blue.svg)](https://galaxy.ansible.com/systemli/etherpad/)

Role to install & maintain Etherpad Lite.

Role Variables
--------------

The playbook requires special configuration. You must set the `etherpad_api_key`!

Defaults: see `defaults/main.yml`

Dependencies
---------------

 * geerlingguy.nodejs

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: systemli.etherpad }

Testing & Development
---------------------

Tests
-----
For developing and testing the role we use Github Actions, Molecule, and Vagrant. On the local environment you can easily test the role with

Run local tests with:

```
molecule test
```

Requires Molecule, Vagrant and `python-vagrant` to be installed.

License
-------

GPLv3

Author Information
------------------

https://www.systemli.org
