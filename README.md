[![CI](https://github.com/de-it-krachten/ansible-role-php/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-php/actions?query=workflow%3ACI)


# php

Manages php



## Dependencies

#### Roles
None

#### Collections

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
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

# Settings to configure in /etc/php.ini
php_ini_settings:
  date.timezone: Europe/Amsterdam
  post_max_size: 25M
  upload_max_filesize: 25M
</pre></code>

### defaults/family-Debian.yml
<pre><code>
# name of the php socket
php_socket: /run/php/php{{ php_version }}-fpm.sock

# OS specific packages
php_packages_os:
  - libapache2-mod-php

# php-fpm service
php_fpm_service: "php{{ php_version }}-fpm"

# apache service
php_apache_service: apache2
</pre></code>

### defaults/family-Suse.yml
<pre><code>
# name of the php socket
php_socket: /var/run/php-fpm/www.sock

# OS specific packages
php_packages_os: []

# php-fpm service
php_fpm_service: "php-fpm"

# apache service
php_apache_service: httpd
</pre></code>

### defaults/family-RedHat.yml
<pre><code>
# name of the php socket
php_socket: /var/run/php-fpm/www.sock

# OS specific packages
php_packages_os: []

# php-fpm service
php_fpm_service: "php-fpm"

# apache service
php_apache_service: httpd
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'php'
  hosts: all
  become: 'yes'
  vars:
    openssl_fqdn: server.example.com
    apache_fqdn: server.example.com
    apache_ssl_key: '{{ openssl_server_key }}'
    apache_ssl_crt: '{{ openssl_server_crt }}'
    apache_ssl_chain: '{{ openssl_server_crt }}'
  roles:
    - deitkrachten.openssl
    - deitkrachten.apache
  tasks:
    - name: Include role 'php'
      ansible.builtin.include_role:
        name: php
</pre></code>
