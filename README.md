# docker-php-web-app
A Docker setup for running a PHP7 web app.

Exposes an Nginx web server that runs PHP scripts through PHP-FPM, along with a MySQL 5.7 database and Adminer.

Each service is configured as a Docker container, following the approach presented in [this great tutorial](https://www.pascallandau.com/blog/php-php-fpm-and-nginx-on-docker-in-windows-10).

By default, Nginx server is mapped to port 51321 and Adminer to port 51322.

The `../` directory is mounted on `/var/www/` both in Nginx and PHP-FPM containers and, by default, Nginx serves all PHP files located at `../public/`. 

The `../database` is mounted on `/var/lib/mysql` for persisting data between container restarts. It's  important that this directory exists before starting up the containers or the database won't be persisted between restarts!

Note that all paths are relative to the directory where this repo was cloned.   

For example, consider a typical PHP webapp having the following file structure:
```
.docker/
config/
database/
public/
  index.php
  about.html   
src/
tmp/
vendor/
composer.json
composer.lock
``` 
where the present repo was cloned in `.docker` directory. In this case, all files and folders alongside `.docker` are mounted into `/var/www/` directory in both Nginx and PHP-FPM containers, and Nginx serves files located at `public/`, while MySQL datafiles will be located under `database/`.

## Suggested reading

[Official PHP Docker Image documentation](https://hub.docker.com/_/php)
[Official Nginx Docker Image documentation](https://hub.docker.com/_/nginx)
[Official MySQL Docker Image documentation](https://hub.docker.com/_/mysql)
[Official Adminer Docker Image documentation](https://hub.docker.com/_/adminer)
