# ansible-playbook-influxdb

Ansible role for deploying the [Influxfb](https://github.com/influxdb/influxdb) time series database

### Requirements

The following ansible variables are used by this role - the default values are shown alongside.

```
* influxdb_version: latest # The version of `influxdb` to install.
* influxdb_admin_user: root # The administrator account for `influx_db`
* influxdb_admin_password: root # the password for `influxdb_admin_user` account.
* influxdb_database: testdb # Role will create a database of this name owned by
  influxdb_user.
* influxdb_user: someuser # A non-privliged database user account for `influxdb_database`.
* influxdb_password: somepassword # the password for `influxdb_user` account.
* influxdb_http_auth_enabled: false # to disable or `true` to enable http authentication.
* influxdb_retention_period: INF # for infinite retention, durations such as 1h, 90m, 12h, 7d, and 4w, are all supported
```

You will want to override these role variables within your playbooks.

### Usage

```
- hosts: "{{ hosts_prefix }}-*"
  sudo: yes
  roles:
    - influxdb
```
