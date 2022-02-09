# ansible-role-etherpad


[![Build Status](https://github.com/systemli/ansible-role-etherpad/workflows/Integration/badge.svg?branch=main)](https://github.com/systemli/ansible-role-etherpad/actions?query=workflow%3AIntegration)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-etherpad-blue.svg)](https://galaxy.ansible.com/systemli/etherpad/)

Role to install, configure & maintain Etherpad Lite. You can use this role to configure Etherpad with those storage solutions : MySQL (or MariaDB), Redis and PostgreSQL.


Currently only MySQL allows to create the user and database. For PostgreSQL those operations should be done by your own (If you want or need to automate those tasks, you can probably use this role : geerlingguy.postgresql).

This playbook also allows to install some plugins for Etherpad :
  - ep_delete_after_delay (To delete some inactive pad after a delay)
  - ep_headerauth (To authenticate users through the HTTP header - Eg usefull when using an SSO portal like LemonLDAP::NG)

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

    etherpad_plugins
List of plugins we want to add to our Etherpad instance.

    etherpad_headerauth_username_header: x-authenticated-user
    etherpad_headerauth_displayname_header: x-authenticated-name
Configuration values for the [ep_headerauth](https://www.npmjs.com/package/ep_headerauth) plugin (authentication with http header). If you want to use this plugin, `etherpad_trust_proxy` and `etherpad_require_authentication` must be set to True.

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
