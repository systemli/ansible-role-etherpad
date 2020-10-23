# ansible-role-etherpad


[![Build Status](https://github.com/systemli/ansible-role-etherpad/workflows/Molecule/badge.svg?branch=master)](https://github.com/systemli/ansible-role-etherpad/actions?query=workflow%3AMolecule)
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

Tests
-----

For developing and testing the role we use Travis CI, Molecule and Vagrant. On the local environment you can easily test the role with

```
pip install molecule-vagrant ansible-lint yamllint
molecule test
```

This requires [Vagrant](https://www.vagrantup.com/downloads.html) to be installed.

License
-------

GPLv3

Author Information
------------------

https://www.systemli.org
