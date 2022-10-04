# Programming Notes
### >> PHP8.0 Extension Modules with PhpMyadmin
Sudo apt update<br>
sudo apt install phpmyadmin php8.0-mbstring php8.0-zip php8.0-gd php-json php8.0-curl<br>

### >> Create new User Mysql
CREATE USER 'user'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';<br>

GRANT ALL PRIVILEGES ON *.* TO 'demo_user'@'localhost' WITH GRANT OPTION;<br>
Flush Privileges;<br>

