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
  become: no

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

  roles:
    - javaguirre.drupal_deps
```

## Usage together with Drupal and Drush installation roles

```yaml
- hosts: all
  remote_user: myuser
  become: no

  vars:
    # geerlingguy.drupal
	drupal_core_version: 7.x
	drupal_domain: "drupaltest.dev"
	drupal_site_name: "Drupal Example"
	drupal_admin_name: admin
	drupal_admin_password: admin
	drupal_webserver_daemon: nginx
	# ...

    # geerlingguy.drush
	drush_install_path: /usr/local/share/drush
	drush_path: /usr/local/bin/drush
	drush_version: master
	# ...

    # javaguirre.drupal_deps
    drush_bin_path: "{{ drush_path }}"
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

  roles:
    - geerlingguy.drupal
    - geerlingguy.drush
    - javaguirre.drupal_deps
```

## Feedback

[Please send me your requests/questions!](https://github.com/javaguirre/ansible-drupal-dependencies-role/issues)

[drupal]: https://github.com/geerlingguy/ansible-role-drupal
[drush]: https://github.com/geerlingguy/ansible-role-drush
