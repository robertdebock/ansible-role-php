php
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-php"><img src="https://travis-ci.org/robertdebock/ansible-role-php.svg?branch=master" alt="Build status" align="left"/></a>

Install and configure php on your system.

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.httpd
    - robertdebock.php
```

The machine you are running this on, may need to be prepared.
```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - robertdebock.bootstrap
    - robertdebock.epel
    - robertdebock.python_pip
    - robertdebock.buildtools
    - robertdebock.httpd
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for php

# Alpine has both php5 and php7. Select the desired version here.
php_alpine_version: 7

# All the settings for PHP.
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

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.buildtools
- robertdebock.epel
- robertdebock.httpd
- robertdebock.scl
- robertdebock.python_pip

```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/php.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.7|ansible 2.8|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|yes|yes|yes*|
|alpine-latest|yes|yes|yes*|
|archlinux|yes|yes|yes*|
|centos-6|no|no|no*|
|centos-latest|yes|yes|yes*|
|debian-latest|yes|yes|yes*|
|debian-stable|yes|yes|yes*|
|debian-unstable*|yes|yes|yes*|
|fedora-latest|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes*|
|opensuse-leap|yes|yes|yes*|
|ubuntu-devel*|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes*|
|ubuntu-rolling|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-php) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-php/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
