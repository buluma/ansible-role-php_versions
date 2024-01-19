# Ansible role [php_versions](https://galaxy.ansible.com/ui/standalone/roles/buluma/php_versions/documentation)

Allows different PHP versions to be installed.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-php_versions/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-php_versions/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-php_versions.svg)](https://github.com/buluma/ansible-role-php_versions/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-php_versions.svg)](https://github.com/buluma/ansible-role-php_versions/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-php_versions.svg)](https://github.com/buluma/ansible-role-php_versions/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/php_versions)](https://galaxy.ansible.com/ui/standalone/roles/buluma/php_versions/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-php_versions/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  vars:
    php_enable_webserver: false

  pre_tasks:
    - name: Update apt cache.
      apt: update_cache=true cache_valid_time=600
      when: ansible_os_family == 'Debian'

  roles:
    - role: geerlingguy.repo-remi
      when: ansible_os_family == 'RedHat'
    - role: buluma.php_versions
    - role: buluma.php

  post_tasks:
    - name: Confirm PHP version is correct.
      shell: php -v | grep -F '{{ php_version }}'
      changed_when: false
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-php_versions/blob/master/defaults/main.yml):

```yaml
---
# The PHP version to be installed.
php_version: '7.4'

# For Debian OSes only.
php_versions_install_recommends: false
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-php_versions/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[geerlingguy.repo-remi](https://galaxy.ansible.com/buluma/geerlingguy.repo-remi)|[![Ansible Molecule](https://github.com/buluma/geerlingguy.repo-remi/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/geerlingguy.repo-remi/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/geerlingguy.repo-remi.svg)](https://github.com/shadowwalker/geerlingguy.repo-remi)|
|[buluma.php_versions](https://galaxy.ansible.com/buluma/php_versions)|[![Ansible Molecule](https://github.com/buluma/ansible-role-php_versions/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-php_versions/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-php_versions.svg)](https://github.com/shadowwalker/ansible-role-php_versions)|
|[buluma.php](https://galaxy.ansible.com/buluma/php)|[![Ansible Molecule](https://github.com/buluma/ansible-role-php/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-php/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-php.svg)](https://github.com/shadowwalker/ansible-role-php)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-php_versions/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|

The minimum version of Ansible required is 2.4, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-php_versions/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-php_versions/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-php_versions/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

