# inachis-docker
Docker config for running inachis

Drop into your project folder, and add docker-compose.yaml to your .gitignore. You can also locate these files elsewhere and update paths to reflect where your project is located.

It will use environment variables from your site to name the containers, and to determine credentials for use with MariaDB. It is expected that `public/` and `bin/console` must exist also.

**Example .env**
```
APP_ENV=dev
APP_NAME=mytestsite
TZ="Europe/London"

…

DB_HOST=localhost
DB_PORT=3306
MYSQL_DATABASE="mysite_db"
MYSQL_USER="username"
MYSQL_PASSWORD="$ecreT123"
MYSQL_ROOT_PASSWORD=""
```

If you decide to use a domain other than `inachis.dev` for your local development, then you will need to update the URL in `docker/apache/httpd-ssl.conf`. The `server.cert` and `server.key` files are empty and will need replacing with you own, such as generatinh a self-signed certificate and key using:

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout server.key -out server.crt
```
