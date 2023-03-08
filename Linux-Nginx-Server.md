#Linux Server
 - df -h
 - htop
 - du [directory]
 - 


## Copy a file from server to local SSH
- Open terminal from to location
- sudo scp username:host:/from_location /to_location


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
        
        
