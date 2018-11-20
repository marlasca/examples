# Install Drupal
Prerequisites: PHP + MYSQL

Install Composer if not installed --> https://getcomposer.org/doc/00-intro.md

Download Drupal creating my_site_name_dir folder (this installation adds Drush and Drupal Console), from your public_html folder.
```
composer create-project drupal-composer/drupal-project:8.x-dev my_site_name_dir --stability dev --no-interaction
```
Create database, for example, with phpmyadmin, and take note of the important data

https://www.drupal.org/docs/8/install/step-3-create-a-database

Configure Drupal and take note of the important data.

http://localhost/my_site_name_dir/web/core/install.php

Check status:

http://localhost/my_site_name_dir/web/admin/reports/status

TRUSTED HOST SETTINGS-->Not enabled
```
cd my_site_name_dir
chmod u+w web/sites/default/settings.php
```
Edit settings.php --> trusted_host_patterns
```
 $settings['trusted_host_patterns'] = array(
  '^localhost$',
 );
```
```
chmod a-w web/sites/default/settings.php
```
## Install the required modules:
```
composer require drupal/admin_toolbar
drush en admin_toolbar -y
```
