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
- RockyLinux 9
- OracleLinux 8
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# php version
php_version: 7.4

# php release
php_release: php74

# php.ini location
php_ini: /etc/php.ini

# Default PHP packages
php_packages:
  - php
  - php-common
  - php-curl
  - php-fpm
  - php-gd
  - php-gmp
  - php-intl
  - php-json
  - php-mbstring
  - php-mysqlnd
  - php-xml
  - php-zip

# Additional PHP packages
php_packages_additional: []
</pre></code>


### vars/family-RedHat.yml
<pre><code>
# name of the php socket
php_socket: /var/run/php5-fpm.sock

# OS specific packages
php_packages_os: []
</pre></code>

### vars/family-Debian.yml
<pre><code>
# name of the php socket
php_socket: /var/run/php/php-fpm.sock

# OS specific packages
php_packages_os:
  - libapache2-mod-php
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'php'
  hosts: all
  become: "{{ molecule['converge']['become'] | default('yes') }}"
  tasks:
    - name: Include role 'php'
      include_role:
        name: php
</pre></code>
