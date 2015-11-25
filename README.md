percona-server
=========

Set up a [percona-server](https://www.percona.com/software/mysql-database/percona-server) server in Debian-like systems.

There are few roles already, however this one is simple, really simple no extra bullshit.

Requirements
------------

* `python-mysqldb` (auto-installed)

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

* `percona_server_version`: [default: `5.6`]: Version to install
* `percona_server_root_password`: [default: undefined]: Root password **required**
* `percona_server_databases`: [default: empty]: List of databases ([mysql_db](http://docs.ansible.com/ansible/mysql_db_module.html) list)
* `percona_server_users`: [default: empty]: List of users ([mysql_user](http://docs.ansible.com/ansible/mysql_user_module.html) list)
* `percona_server_config`: [default: empty]: Configuration dictionary (mysqld section of my.cnf)

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

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
