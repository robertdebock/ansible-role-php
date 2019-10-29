php
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-php"><img src="https://travis-ci.org/robertdebock/ansible-role-php.svg?branch=master" alt="Build status" align="left"/></a>

Install and configure php on your system.

<img src="https://img.shields.io/ansible/role/d/23465"/>
<img src="https://img.shields.io/ansible/quality/23465"/>

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
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.python_pip
    - role: robertdebock.buildtools
    - role: robertdebock.httpd
    - role: robertdebock.remi
      remi_enabled_repositories:
        - php73
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
- robertdebock.remi

```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/php.png "Dependency")


Compatibility
-------------

This role has been tested on these [container images](https://hub.docker.com/):

|container|tag|allow_failures|
|---------|---|--------------|
|alpine|latest|no|
|alpine|edge|yes|
|debian|stable|yes|
|debian|unstable|yes|
|debian|latest|no|
|centos|latest|no|
|fedora|latest|no|
|fedora|rawhide|yes|
|opensuse|latest|no|
|ubuntu|rolling|yes|
|ubuntu|devel|yes|
|ubuntu|latest|no|

This role has been tested on these Ansible versions:

- ansible~=2.7
- ansible~=2.8
- git+https://github.com/ansible/ansible.git@devel

The indicator '\~=' means [compatible with](https://www.python.org/dev/peps/pep-0440/#compatible-release). For example 'ansible\~=2.8' would pick the latest ansible-2.8, for example ansible-2.8.6.




Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-php) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-php/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

Modules
-------

This role uses the following modules:
```yaml
---
- ini_file
- package
```

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
