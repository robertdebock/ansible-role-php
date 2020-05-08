# php

Install and configure php on your system.

|Travis|GitHub|Quality|Downloads|
|------|------|-------|---------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-php.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-php)|[![github](https://github.com/robertdebock/ansible-role-php/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-php/actions)|[![quality](https://img.shields.io/ansible/quality/23465)](https://galaxy.ansible.com/robertdebock/php)|[![downloads](https://img.shields.io/ansible/role/d/23465)](https://galaxy.ansible.com/robertdebock/php)|

## Example Playbook

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.httpd
    - role: robertdebock.php
```

The machine may need to be prepared using `molecule/resources/prepare.yml`:
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
```

For verification `molecule/resources/verify.yml` run after the role has been applied.
```yaml
---
- name: Verify
  hosts: all
  become: yes
  gather_facts: yes

  tasks:
    - name: check if connection still works
      ping:
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## Role Variables

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

## Requirements

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

## Dependencies

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- robertdebock.httpd
## Context

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/php.png "Dependency")

## Compatibility

This role has been tested on these [container images](https://hub.docker.com/):

|container|tags|
|---------|----|
|alpine|all|
|el|7, 8|
|debian|buster, bullseye|
|fedora|31, 32|
|opensuse|all|
|ubuntu|focal, bionic, xenial|

The minimum version of Ansible required is 2.8 but tests have been done to:

- The previous version, on version lower.
- The current version.
- The development version.

## Exceptions

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| Alpine | ImportError: Error loading shared library /tmp/pip-build-env-zrX8Lu/lib/python2.7/site-packages/_cffi_backend.so: Operation not permitted |


## Testing

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-php) are done on every commit, pull request, release and periodically.

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

## License

Apache-2.0


## Author Information

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
