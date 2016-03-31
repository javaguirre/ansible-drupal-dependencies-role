# Drupal dependencies Ansible role

[![Build Status](https://travis-ci.org/javaguirre/ansible-drupal-dependencies-role.svg?branch=master)](https://travis-ci.org/javaguirre/ansible-drupal-dependencies-role)

Ansible role using [Drush](https://github.com/drush-ops/drush) to manage theme and module dependencies in **Drupal**.

## Dependencies

This role doesn't install Drupal nor Drush, there are other roles already doing that, for example you could use geerlingguy's
Ansible modules for that purpose:

- [Drupal][drupal]
- [Drush][drush]

## Variables

List of variables and default values:

```yaml
drush_bin_path: ""
drupal_path: "/var/www/drupal"
drupal_user: apache
drupal_core_modules: []
drupal_themes: []
drupal_modules: []
drupal_other_modules: []
drupal_default_theme: bartik
drupal_clear_cache: no
drupal_cache_option: all
```

## Usage

An example usage could be like:

```yaml
- hosts: all
  remote_user: myuser
  sudo: no

  vars:
    drush_bin_path: "/usr/bin/drush"
    drupal_user: http
    drupal_core_modules:
      - contact

    drupal_themes:
      - bootstrap

    drupal_modules:
      - ctools
      - entity
      - ldap

    drupal_other_modules:
      - simpletest

    drupal_default_theme: bootstrap

    drupal_clear_cache: yes
    drupal_cache_option: theme
```

## Feedback

[Please send me your requests/questions!](https://github.com/javaguirre/ansible-drupal-dependencies-role/issues)

[drupal]: https://github.com/geerlingguy/ansible-role-drupal
[drush]: https://github.com/geerlingguy/ansible-role-drush
