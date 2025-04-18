## Ansible Role: MariaDB

Ansible role to install and configure MariaDB on Debian 10+. Additionally, configures nightly SQL backups of all databases (excluding default databases) to a local folder.

- The installation is secured. equivilent to running ```secure_mysql_installation```. 
- Backups are stored locally under ```/opt/mysql-backup/``` and retained and rotated for 14 days by default.
- It's recommended backup files are periodically pulled off-host as part of your disaster recovery (DR) plan.

The following packages will be installed when this role executes:

- mariadb-server
- mariadb-client
- mariadb-common
- python3-pymysql
- bzip2

## Actions Performed

1. Installs MariaDB; the following packages are installed:
   - mariadb-server
   - mariadb-client
   - mariadb-common
   - python3-pymysql
   - bzip2
2. Configures MariaDB to allow remote connections.
3. Secures MariaDB install.
4. Configures nightly SQL backups.

## Setup Instructions

### Clone Repository

Clone the project into the roles directory of your Ansible Controller.

```bash
git clone https://github.com/twobyteblog/lets_linux.git
```

### Variables

Within your Ansible environment, add the following variables:

```bash
mysql_root_password: mypassword
```

By default 14 days worth of backups will be retained. This can be modified by overwriting the role's default variables within your group/hosts variables.

```bash
mysql_days_to_keep: 14
```

### PlayBook

Create a playbook which runs this role. This role requires ```become``` privileges.

```
- hosts: mariadb
  roles:
    - role: ansible_mariadb
      become: yes
```
