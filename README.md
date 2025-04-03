# inachis-docker
Docker config for running inachis

Drop into your project folder, and add docker-compose.yaml to your .gitignore. You can also locate these files elsewhere and update paths to reflect where your project is located.

It will use environment variables from your site to name the containers, and to determine credentials for use with MariaDB. It is expected that `public/` and `bin/console` must exist also.

**Example .env**
```
APP_ENV=dev
APP_NAME=mytestsite

…

DB_HOST=localhost
DB_PORT=3306
MYSQL_DATABASE="mysite_db"
MYSQL_USER="username"
MYSQL_PASSWORD="$ecreT123"
MYSQL_ROOT_PASSWORD=""
```
