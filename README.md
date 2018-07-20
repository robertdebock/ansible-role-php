php
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-php.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-php)

Provides PHP for your system.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/php.png "Dependency")

Requirements
------------

Access to a repository containing packages, likely on the internet.

Role Variables
--------------

- php_alpine_version: For alpine, use PHP 5 or 7.

Many can be set, for example:
```
php_settings:
  display_errors:
    section: PHP
    value: "Off"
  display_startup_errors:
    section: PHP
    value: "Off"
  error_reporting:
    section: PHP
    value: "Off"
  html_errors:
    section: PHP
    value: "On"
  log_errors:
    section: PHP
    value: "On"
  max_input_time:
    section: PHP
    value: 60
  output_buffering:
    section: PHP
    value: 4096
  register_argc_argv:
    section: PHP
    value: "Off"
  request_order:
    section: PHP
    value: GP
  session.bug_compat_42:
    section: PHP
    value: "Off"
  session.bug_compat_warn:
    section: PHP
    value: "Off"
  session.gc_divisor:
    section: PHP
    value: 1000
  session.hash_bits_per_character:
    section: PHP
    value: 5
  short_open_tag:
    section: PHP
    value: "Off"
  track_errors:
    section: PHP
    value: "Off"
  variables_order:
    section: PHP
    value: GPCS
  Engine:
    section: PHP
    value: "On"
  date.timezone:
    section: Date
    value: Europe/Amsterdam
  memory_limit:
    section: PHP
    value: 128M
```

Dependencies
------------

You can use this role to prepare your system:

- [robertdebock.bootstrap](https://travis-ci.org/robertdebock/ansible-role-bootstrap)
- [robertdebock.buildtools](https://travis-ci.org/robertdebock/ansible-role-buildtools)
- [robertdebock.epel](https://travis-ci.org/robertdebock/ansible-role-epel)
- [robertdebock.httpd](https://travis-ci.org/robertdebock/ansible-role-httpd)
- [robertdebock.python_pip](https://travis-ci.org/robertdebock/ansible-role-python_pip)


Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.4|ansible 2.5|ansible 2.6|
|------------|-----------|-----------|-----------|
|alpine-edge|yes|yes|yes|
|alpine-latest|yes|yes|yes|
|archlinux|yes|yes|yes|
|centos-6|no|no|no|
|centos-latest|yes|yes|yes|
|debian-latest|yes|yes|yes|
|debian-stable|yes|yes|yes|
|fedora-latest|yes|yes|yes|
|fedora-rawhide|yes|yes|yes|
|opensuse-leap|yes|yes|yes|
|opensuse-tumbleweed|yes|yes|yes|
|ubuntu-artful|yes|yes|yes|
|ubuntu-latest|yes|yes|yes|

Example Playbook
----------------

```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.scl
    - role: robertdebock.buildtools
    - role: robertdebock.python_pip
    - role: robertdebock.httpd
    - role: robertdebock.php
```

Install this role using `galaxy install robertdebock.php`.

License
-------

Apache License, Version 2.0

Author Information
------------------

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
