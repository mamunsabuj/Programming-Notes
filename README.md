# Programming Notes
#### =================
### PHP8.0 Extension Modules with PhpMyadmin
### ===================
Sudo apt update
sudo apt install phpmyadmin php8.0-mbstring php8.0-zip php8.0-gd php-json php8.0-curl

Create new User Mysql
===============
CREATE USER 'user'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

GRANT ALL PRIVILEGES ON *.* TO 'demo_user'@'localhost' WITH GRANT OPTION;
Flush Privileges;

