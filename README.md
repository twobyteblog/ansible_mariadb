# Ansible Role: MariaDB

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

