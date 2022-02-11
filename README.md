# ansible-role-etherpad


[![Build Status](https://github.com/systemli/ansible-role-etherpad/workflows/Integration/badge.svg?branch=main)](https://github.com/systemli/ansible-role-etherpad/actions?query=workflow%3AIntegration)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-etherpad-blue.svg)](https://galaxy.ansible.com/systemli/etherpad/)

Role to install, configure & maintain Etherpad Lite. You can use this role to configure Etherpad with those storage solutions : MySQL (or MariaDB), Redis and PostgreSQL.


Currently only MySQL allows to create the user and database. For PostgreSQL those operations should be done by your own (If you want or need to automate those tasks, you can probably use this role : geerlingguy.postgresql).

Role Variables
--------------

The playbook requires special configuration. You must set the `etherpad_api_key`!

    etherpad_db_type: dirty
This variable allows to define what kind of backend storage we want to use for Etherpad (default is [dirty](https://github.com/felixge/node-dirty), please don't use this value in production environment). This variable must be set to one of those values : dirty, mysql, redis or postgres.

    etherpad_postgres_database_host: localhost
    etherpad_postgres_database_name: etherpad
    etherpad_postgres_database_user: etherpad
    etherpad_postgres_database_password:
    etherpad_postgres_database_port: 5432
    etherpad_postgres_database_ssl_policy: "disabled"
Those variables allow to configure Etherpad with PostgreSQL. To be able to use them, you must set the variable `etherpad_db_type` to `postgres`.

For more information about available variables (and their default values) : see `defaults/main.yml`

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
