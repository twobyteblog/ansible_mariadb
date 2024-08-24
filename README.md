# Ansible Role: MariaDB

Ansible role which installs MariaDB on a Debian 10+ and configures nightly SQL backups of all databases (excluding default databases).

- The installation is secured equivilent to running ```secure_mysql_installation```. 
- Backups are stored locally under ```/opt/mysql-backup/``` and retained/rotated for 14 days by default.
- It's recommended backup files are periodically pulled off-site as part of your disaster recovery (DR) plan.

The following packages will be installed when this role executes:

- mariadb-server
- mariadb-client
- mariadb-common
- python3-pymysql
- bzip2

# Requirements

This role requires root access to the host system. Specify it globally, or add it to your playbook (example below).

```
- hosts: mariadb
  roles:
    - role: ansible_mariadb
      become: yes
```

# Role Variables

To use this role, specify a mysql root password within your host variables.

```
mysql_root_password: mypassword
```

# Installation

To use this role, clone it into the directory containing your other Ansible roles.

```
git clone https://github.com/inundationca/ansible_mariadb.git
```

Next, add it to an new or existing playbook.

```
- hosts: mariadb
  roles:
    - role: ansible_mariadb
      become: yes
```

By default 14 days worth of backups will be retained. This can be modified by overwriting the role's default variables within your group/hosts variables.

```
mysql_days_to_keep: 14
```

