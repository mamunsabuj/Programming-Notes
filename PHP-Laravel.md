# PHP Notes

## Composer dependency issue solving
composer install --ignore-platform-reqs
composer install --ignore-platform-req=php

####Ref
https://php.watch/articles/composer-ignore-platform-req

## Laravel Storage File Permission
a. sudo chown www-data:www-data -R storage/
b. sudo chown www-data:www-data -R bootstrap/cache/
## php7.4-fpm Restart
sudo service php7.4-fpm restart
