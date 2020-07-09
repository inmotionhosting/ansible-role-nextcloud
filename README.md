inmotionhosting.nextcloud
=========

Modular Ansible Role for deploying and configuring Nextcloud.

[![Build Status](https://travis-ci.org/inmotionhosting/ansible-role-nextcloud.png?branch=master)](https://travis-ci.org/inmotionhosting/ansible-role-nextcloud)

Requirements
------------

* CentOS 7.x or later
* Debian 9 or later
* Ubuntu 16.04 LTS or later

Role Variables
--------------

### Defaults
Variables in `defaults/main.yml`

| Variable | Definition |
| -------- | ---------- |
| pass_gen_alias | A variable acting as an alias to generate safe passwords.
| site_domain | The domain to associate with the Nextcloud installation.
| site_user | The username to associated with the Nextcloud administrative account.
| site_pass | The password to associated with the Nextcloud administrative account.
| system_user | The system user that the Nextcloud installation will belong to.
| database_connector | The database in use (e.g. MySQL, PostgreSQL)
| nc_db_name | The name of the database to associate with this Nextcloud installation.
| nc_db_user | The name of the database user account to associate with this Nextcloud installation.
| nc_db_pass | (Optional) The password to associate with the `nc_db_user`.  If not defined, the password will be automatically generated via `pass_gen_alias`.
| nc_system_folder | The full path to the Nextcloud installation's document root
| nc_system_path | The home directory for `system_user`
| max_request_workers | Apache: The number of simultaneously connections allowed. Must be a multiple of 25.
| php_proc_mem: | PHP-FPM: Memory consumption per PHP worker.
| children_buffer | PHP-FPM: What percentage of the server's memory PHP can consume.


Dependencies
------------

### Required

```yaml
- role: inmotionhosting.apache
- role: inmotionhosting.postgresql
- role: inmotionhosting.php_fpm
```

Example Playbook
----------------

```yaml
- hosts: nextcloud
  roles:
    - role: ansible-role-apache
    - role: ansible-role-postgresql
    - role: ansible-role-php_fpm
    - role: ansible-role-nextcloud
```

License
-------

GPLv3

Author Information
------------------

[InMotion Hosting](https://inmotionhosting.com)
