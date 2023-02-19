
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


