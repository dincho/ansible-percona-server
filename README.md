[![Build Status](https://travis-ci.org/dincho/ansible-percona-server.svg?branch=master)](https://travis-ci.org/dincho/ansible-percona-server)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-published-blue.svg)](https://galaxy.ansible.com/detail#/role/6246)

percona-server
=========

Set up a [percona-server](https://www.percona.com/software/mysql-database/percona-server) server in Debian-like systems.

There are few roles already, however this one is simple, really simple no extra bullshit.

Requirements
------------

* `python-mysqldb` (auto-installed)

Role Variables
--------------

* `percona_server_version`: [default: `5.7`]: Version to install
* `percona_server_root_password`: [default: undefined]: Root password (**required**)
* `percona_server_databases`: [default: empty]: List of databases ([mysql_db](http://docs.ansible.com/ansible/mysql_db_module.html) list)
* `percona_server_users`: [default: empty]: List of users ([mysql_user](http://docs.ansible.com/ansible/mysql_user_module.html) list)
* `percona_server_config`: [default: empty]: Configuration dictionary (mysqld section of my.cnf)

Dependencies
------------

None

Example Playbook
----------------
    - hosts: servers
      vars:
        percona_server_root_password: mysql_root_pass
        percona_server_databases:
          - { name: database1 }
        percona_server_users:
          - { name: user1, password: sapun, priv: "database1.*:ALL" }
        percona_server_config:
          bind-address: "0.0.0.0"
          performance_schema: "off"
      roles:
         - dincho.percona-server

License
-------

MIT
