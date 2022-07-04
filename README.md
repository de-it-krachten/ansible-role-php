[![CI](https://github.com/de-it-krachten/ansible-role-php/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-php/actions?query=workflow%3ACI)


# php

Manages php


## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- OracleLinux 8
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 35
- Fedora 36

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# php version
php_version: 7.4

# php release
php_release: php74
</pre></code>

### vars/family-RedHat.yml
<pre><code>
# php.ini location
php_ini: /etc/php.ini

# name of the php socket
php_socket: /var/run/php5-fpm.sock

# list of php packages
php_packages:
  - php
  - php-common
  - php-json
  - php-xml
  - php-fpm
  - php-mbstring
  # - php-imap
  # - php-pear-DB
  - php-mysqlnd
  - php-gmp
  # - php-intl
</pre></code>

### vars/family-Debian.yml
<pre><code>
# php.ini location
php_ini: /etc/php.ini

# name of the php socket
php_socket: /var/run/php/php-fpm.sock

# list of php packages
php_packages:
  - php
  - php-curl
  - php-common
  - php-json
  - php-xml
  - php-fpm
  - php-mbstring
  - php-mysqlnd
  - php-gmp
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'php'
  hosts: all
  vars:
  tasks:
    - name: Include role 'php'
      include_role:
        name: php
</pre></code>
