#Linux Server
 - df -h
 - htop
 - du [directory]
 - 


## Copy a file from server to local SSH
- Open terminal from to location
- sudo scp username:host:/from_location /to_location

## Laravel Storage Permission Change
 sudo chown www-data:www-data -R storage/
 sudo chown www-data:www-data -R bootstrap/cache/
 php artisan storage:link
 
 restart PHP FPM
 sudo service php7.4-fpm restart


## Default Nginx Virtual host 

server {
        server_name example.stylezworld.net;
        root /var/www/html/example.com/public;

        add_header X-Frame-Options "SAMEORIGIN";
        add_header X-XSS-Protection "1; mode=block";
        add_header X-Content-Type-Options "nosniff";

        index index.php;

        charset utf-8;

        location / {
                try_files $uri $uri/ /index.php?$query_string;
        }

        location = /favicon.ico { access_log off; log_not_found off; }
        location = /robots.txt  { access_log off; log_not_found off; }

        error_page 404 /index.php;

        location ~ \.php$ {
                fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
                fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
                include fastcgi_params;
        }

        location ~ /\.(?!well-known).* {
                deny all;
        }
}

## Nginx Vertual Host
### Nginx 
- sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
- sudo ln -s /etc/nginx/sites-available/test.com /etc/nginx/sites-enabled/
  ### Install SSL
  - sudo certbot --nginx -d example.com -d www.example.com
  - For Auto Renewal   sudo systemctl status certbot.timer


## Nginx Setup and Configuration
apt install nginx


#Install PHP Extensions

sudo apt-get install php7.0-curl
sudo apt-get install php7.0-dom
sudo apt-get install php7.0-mcrypt
sudo apt-get install php7.0-simplexml
sudo apt-get install php7.0-spl
sudo apt-get install php7.0-xsl
sudo apt-get install php7.0-intl
sudo apt-get install php7.0-mbstring
sudo apt-get install php7.0-ctype
sudo apt-get install php7.0-hash
sudo apt-get install php7.0-openssl
sudo apt-get install php7.0-zip
sudo apt-get install php7.0-xmlwriter
sudo apt-get install php7.0-gd
sudo apt-get install php7.0-iconv



##server phpmyadmin link change 

domain/phpmyadmin - any/any

phpmyadmin location
/etc/apache2/conf-available/phpmyadmin.conf

line 3:

Alias /whateveryouwant /usr/share/phpmyadmin

sudo a2enconf phpmyadmin.conf
sudo service apache2 reload

## PHP 7.2 Extensions Installation
sudo apt-get install php-curl
or
sudo apt-get install php5-curl
or
sudo apt-get install php7.*-curl
sudo apt-get install php7.*-dom
sudo apt-get install php7.*-mcrypt
sudo apt-get install php7.*-simplexml
sudo apt-get install php7.*-spl
sudo apt-get install php7.*-xsl
sudo apt-get install php7.*-intl
sudo apt-get install php7.*-mbstring
sudo apt-get install php7.*-ctype
sudo apt-get install php7.*-hash
sudo apt-get install php7.*-openssl
sudo apt-get install php7.*-zip
sudo apt-get install php7.*-xmlwriter
sudo apt-get install php7.*-gd
sudo apt-get install php7.*-iconv

sudo apt-get install zip
sudo apt-get install unzip

sudo a2enmod rewrite;

#tar a file

Untar a file
tar -zxvf yourfile.tar.gz

#To copy a file from B to A while logged into B:

scp /path/to/file UsernameofA@IPofA:/path/to/destination


#Port Open
=========


https://www.youtube.com/watch?v=5cZA1Y6ZTgA
Port List:

ufw status
sudo ufw status numbered

sudo netstat -tuplen

Open Port:
sudo ufw allow 1191/tcp

Restart Firewall:

sudo ufw disable
sudo ufw enable


# # Remove big files directory

sudo find . -name 'PHP*' | xargs rm



### File Copy from one server to another

Syntax:

scp <source> <destination>
To copy a file from B to A while logged into B:

scp /path/to/file username@a:/path/to/destination


To copy a file from B to A while logged into A:

scp username@b:/path/to/file /path/to/destination

## How To Connect to MySQL Managed Database via phpMyAdmin
        
Tutorial:  https://www.digitalocean.com/community/tutorials/how-to-connect-to-mysql-managed-database-via-phpmyadmin
        
### Step 1 — Installing phpMyAdmin and Configuring Apache
        - sudo apt update
        - sudo apt -y install phpmyadmin
        - sudo nano /etc/apache2/apache2.conf
        Add the following line to the bottom of the file:
         phpMyAdmin Configuration
          Include /etc/phpmyadmin/apache.conf
### Step 2 — Configuring phpMyAdmin with MySQL Managed Database
    - Navigate to your MySQL Managed Database panel and find the Connection Details section. Click the Download CA certificate link to download the ca-         certificate.crt file from your database page overview tab:
        
       - scp Downloads/ca-certificate.crt root@your-server-ip:/etc/phpmyadmin
        - sudo nano /etc/phpmyadmin/config.inc.php
        
        Add following lines in bottom
        $i++;
        $cfg['Servers'][$i]['host'] = 'your_database_cluster_hostname.b.db.ondigitalocean.com';
        $cfg['Servers'][$i]['port'] = '25060';
        $cfg['Servers'][$i]['ssl'] = true;
        $cfg['Servers'][$i]['ssl_ca'] = '/etc/phpmyadmin/ca-certificate.crt';
        
        or  another  code
        $i++;
        /* Authentication type */
        $cfg['Servers'][$i]['auth_type'] = 'cookie';
        /* Server parameters */
        $cfg['Servers'][$i]['host'] = 'db-mysql-sgp1-73738-do-user-7928468-0.b.db.ondigitalocean.com:25060';
        $cfg['Servers'][$i]['compress'] = false;
        $cfg['Servers'][$i]['AllowNoPassword'] = true;
        
        - sudo service apache2 restart
 
 
# Perpare A Server for run the Application
#  =========================================
 ## Packages Installation in Ubuntu 20.04 + php7.4
     apt-get update
     apt-get upgrade
     apt-get install software-properties-common
     If there is no git, install git
     apt-get install nginx
     apt-get install mysql-server
     Create user for applications
     mysql --user=root mysql
     CREATE USER dBadmin@'localhost' IDENTIFIED BY 'new-pass';GRANT ALL PRIVILEGES ON *.* TO dBadmin@'localhost' WITH GRANT OPTION;FLUSH PRIVILEGES;
     ALTER USER dBadmin@'localhost' IDENTIFIED WITH mysql_native_password BY 'g0RmG@D0Hs123';
     Exit
     apt-get install php7.4 php7.4-curl php7.4-mbstring php7.4-mysql php7.4-xml php7.4-cli php7.4-fpm php7.4-json php7.4-xsl php7.4-common php7.4-gd php7.4-zip php7.4-intl php7.4-bcmath
     ssh-keygen -t rsa  //(generate ssh key)
     cat .ssh/id_rsa.pub (to show the ssh key)
 
 ## PHP ini update
      cd /etc/php/7.4/fpm
      nano php.ini
      update `max_input_vars = 99999` , `memory_limit = -1`, post_max_size = 300M and upload_max_filesize = 300M
      sudo service php7.4-fpm restart
 
 ## Composer Installation
     php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" php -r "if (hash_file('SHA384', 'composer-setup.php') ==='544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
     php composer-setup.php
     php -r "unlink('composer-setup.php');"
     mv composer.phar /usr/local/bin/composer
     composer -V (to check composer version)
 
 ## Composer Private Package Installation
     Give username and password of someone who have access of the repo
     Token will be stored at location: "/root/.config/composer/auth.json"
     Change user and pass if a user has no access any more.
 
 ## nstall Phpmyadmin
     sudo apt update
     sudo apt install phpmyadmin
     Press tab the enter
     choose Yes for dbconfig-common
     use a password
     type same password again
     Hit enter
 
## Setup Phpmyadmin with nginx
     sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
     cd 
     sudo nano /etc/nginx/sites-available/phpmyadmin
     Write following code:
 
 
         server {
          listen 7070;
          listen [::]:7070;

          #server_name phpmyadmin;

          root /var/www/phpmyadmin;
          index index.html index.php;

          location / {
           try_files $uri $uri/ /index.php?$query_string;
           #try_files $uri $uri/ =404;
          }

          location ~ \.php$ {
           include snippets/fastcgi-php.conf;
           # With php7.0-cgi alone:
           #fastcgi_pass 127.0.0.1:9000;
           # With php7.0-fpm:
           fastcgi_pass unix:/run/php/php7.4-fpm.sock;
          }
         }

         sudo ln -s /etc/nginx/sites-available/phpmyadmin /etc/nginx/sites-enabled/phpmyadmin
         sudo service nginx reload
         phpmyadmin should be running on {host}:7070
 
 ## Site Creation
       cd /var/www
       git clone {repo_url} {domain_name}
       sudo nano /etc/nginx/sites-available/{domain_name}
       fill content with the following code block

       server {
               listen 80;
               listen [::]:80;
               listen 8080;
               client_max_body_size 200M;
               #server_name erp;

               root /var/www/{folder}/public;
               index index.html index.php;

               location / {
                   try_files $uri $uri/ /index.php?$query_string;
                   #try_files $uri $uri/ =404;
               }

               location ~ \.php$ {
                   include snippets/fastcgi-php.conf;
                   # With php7.0-cgi alone:
                   #fastcgi_pass 127.0.0.1:9000;
                   # With php7.0-fpm:
                   fastcgi_read_timeout 300;
                   fastcgi_pass unix:/run/php/php7.4-fpm.sock;
               }
       }


       ln -s /etc/nginx/sites-available/{domain} /etc/nginx/sites-enabled/{domain}
       service nginx reload
 
 
 ## Permissions for laravel app:
    chown www-data:www-data -R storage/
    chown www-data:www-data -R bootstrap/cache/
    php artisan storage:link
 
 ## Scheduler Run in cron:
     sudo crontab -e
     For first time choose 1 for nano editor
     Write at the bottom of the file
     * * * * * cd /var/www/{folder} && php artisan schedule:run >> /dev/null 2>&1
 
 ## MySQL Database Commands:
     Import: “mysql -u username -p database_name < file.sql”
     Export: “mysqldump -u username -p database_name > file.sql”
 
 Copy Local Folder to Remote Server:
     scp -r ‘local_path’ ‘user@server_ip:/server_path’
 
## Install Wkhtmltopdf
    run `wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.focal_amd64.deb`
    run `dpkg -i wkhtmltox_0.12.6-1.focal_amd64.deb`
    run `apt --fix-broken install`
    run `wkhtmltopdf --version` for version checking












