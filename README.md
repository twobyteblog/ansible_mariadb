# Ansible Role: MariaDB

This is a minimal role which installs and secures MariaDB. Additionally as part of this role, a backup script and associated crontab is created to ensure daily local backups of all databases. These backups can than be pulled off using your preferred backup solution. By default, backups will be kept for 14 days before being removed.

Installs and configures MariaDB on a Debian 10+ server.

# Requirements

This role requires root access. Either specify it globally, or add it to your playbook as follows:

```
- hosts: mariadb
  roles:
    - role: ansible_mariadb
      become: yes
```

# Role Variables

This role only requires one variable.

```
mysql_root_password:
```

This variable can be specified under ```vars/main.yml``` or within host/group vars.

# Installation

To install this role, run:

```
git clone https://github.com/inundationca/ansible_mariadb.git
```

Within your host or group vars, specify root credential used to secure the installation.

```
mysql_root_password: mypassword
```

By default the backup script will retain 14 days worth of backups. To change this, you can modify the script stored in files/mysql_backup.sh.

