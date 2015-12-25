# Drupal dependencies Ansible role

[![Build Status](https://travis-ci.org/javaguirre/ansible-drupal-dependencies-role.svg?branch=master)](https://travis-ci.org/javaguirre/ansible-drupal-dependencies-role)

Ansible role using [Drush](https://github.com/drush-ops/drush) to manage theme and module dependencies in **Drupal**.

## Dependencies

This role doesn't install Drupal nor Drush, there are other roles already doing that, you could use this role with those.

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

```

## Feedback

[Please send me your requests/questions!](https://github.com/javaguirre/ansible-drupal-dependencies-role/issues)
