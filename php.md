# nginx
```
server {
  listen 80;
  server_name wp.test;
  root /Users/joey/code/wp;
  index index.php;

  location = /favicon.ico {
    log_not_found off;
    access_log off;
  }

  location = /robots.txt {
    allow all;
    log_not_found off;
    access_log off;
  }

  location / {
    try_files $uri $uri/ /index.php?$args;
  }

  location ~ .php {
    include fastcgi_params;
    fastcgi_pass 127.0.0.1:9000;
    fastcgi_index index.php;
    fastcgi_param SCRIPT_FILENAME /Users/joey/code/wp/$fastcgi_script_name;
  }

  location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
    expires max;
    log_not_found off;
  }
}
```

# phpbrew  
`brew install bzip2 zlib zip mhash mcrypt`
`phpbrew install 7.3 +default +mysql +fpm +bz2=/usr/local/opt/bzip2 +zlib=/usr/local/opt/zlib +zip=/usr/local/opt/libzip`

# fpm
## /Users/joey/.phpbrew/php/php-7.3.11/etc/php-fpm.d/www.conf
`listen = 9000`

# wordpress/mysql
## wp-config.php
`define( 'DB_HOST', 'localhost:/tmp/mysql.sock' );`
