## Service commands

* `service nginx start`
* `service nginx stop`
* `service nginx restart`
* `service nginx reload`

## Overall config

* Located at `/etc/nginx/nginx.conf`
* Includes other files with `include /etc/nginx/sites_enabled/*`

```nginx
user www-data; # Which user runs the server
worker_processes 4; # How many threads to run
pid /run/nginx.pid; # Where to write the process

events {
        worker_connections 768;
        # multi_accept on;
}
http {
    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;

    include /etc/nginx/mime.types;
    default_type application/octet-stream;

    access_log /var/log/nginx/access.log; # Location
    error_log /var/log/nginx/error.log;   # Location

    gzip on;
    gzip_disable "msie6";
}
```

## Virtual host config

* Included in overall config
* Staged servers located at `/etc/nginx/sites-available`
* Live servers located at `/etc/nginx/sites-enabled`
* Symlink staged to live to enable server - `ln -s /etc/nginx/sites-available/file /etc/nginx/sites-enabled/file`

```nginx
server {
    listen 80;
    listen [::]:80;

    root /var/www/ihatethepush;
    index index.html;

    server_name ihatethepush.*;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
