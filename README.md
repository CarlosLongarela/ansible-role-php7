Ansible Role: PHP 7.x
=========

[![Build Status](https://travis-ci.org/CarlosLongarela/ansible-role-php7.svg?branch=master)](https://travis-ci.org/CarlosLongarela/ansible-role-php7)
[![Percentage of issues still open](http://isitmaintained.com/badge/open/CarlosLongarela/ansible-role-php7.svg)](http://isitmaintained.com/project/CarlosLongarela/ansible-role-php7 "Percentage of issues still open")
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/CarlosLongarela/ansible-role-php7.svg)](http://isitmaintained.com/project/CarlosLongarela/ansible-role-php7 "Average time to resolve an issue")

PHP 7.x fpm install and configuration.

Requirements
------------

None.

Role Variables
--------------

    php_version: 7.2
    php_fpm_daemon: "php{{ php_version }}-fpm"

    php_modules:
      - php{{ php_version }}-bz2
      - php{{ php_version }}-curl
      - php{{ php_version }}-gd
      - php{{ php_version }}-json
      - php{{ php_version }}-mbstring
      - php{{ php_version }}-mcrypt
      - php{{ php_version }}-mysql
      - php{{ php_version }}-readline
      - php{{ php_version }}-recode
      - php{{ php_version }}-tidy
      - php{{ php_version }}-xml
      - php{{ php_version }}-xsl
      - php{{ php_version }}-zip
      - php{{ php_version }}-opcache
      - php-imagick

    php_max_input_vars: 1000
    php_memory_limit: 512M
    php_display_errors: Off
    php_post_max_size: 48M
    php_upload_max_filesize: 12M
    php_max_file_uploads: 20
    php_date_timezone: Europe/Madrid
    php_max_execution_time: 30
    php_max_input_time: 60
    php_opcache_enable: 1
    php_opcache_memory_consumption: 64
    php_opcache_max_accelerated_files: 2000
    php_opcache_revalidate_freq: 2
    php_opcache_interned_strings_buffer: 8

    php_fpm_pid: "/run/php/php{{ php_version }}-fpm.pid"
    php_fpm_error_log: "/var/log/php{{ php_version }}-fpm.log"
    php_fpm_process_max: 128

    php_fpm_pool_name: web
    php_fpm_pool_user: www-data
    php_fpm_pool_group: www-data
    php_fpm_pool_mode: "0660"
    php_fpm_pool_listen: "/run/php/php{{ php_version }}-fpm.sock"
    #php_fpm_pool_listen: "127.0.0.1:9000"

    php_fpm_pool_max_children: 10
    php_fpm_pool_start_servers: 5
    php_fpm_pool_min_spare_servers: 3
    php_fpm_pool_max_spare_servers: 6

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers

      gather_facts: no
      become: true

      vars:
        php_max_input_vars: 1000
        php_memory_limit: 512M
        php_display_errors: Off
        php_post_max_size: 48M
        php_upload_max_filesize: 12M
        php_max_file_uploads: 20
        php_date_timezone: Europe/Madrid
        php_max_execution_time: 30
        php_max_input_time: 60
        php_opcache_enable: 1

      roles:
         - { role: CarlosLongarela.php }

License
-------

GPLv2

Author Information
------------------

This role was created in 2017, May by [Carlos Longarela](mailto:carlos@longarela.eu), from [Taberna WordPress](https://tabernawp.com/).
