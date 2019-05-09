# docker-php-web-app
A Docker setup for running a PHP7 web app.

Exposes an Nginx web server that runs PHP scripts through PHP-FPM.

Each service (Nginx, PHP-FPM) is configured as a Docker container, following the approach presented in [this great tutorial](https://www.pascallandau.com/blog/php-php-fpm-and-nginx-on-docker-in-windows-10).

The `../` directory is mounted as a volume into `/var/www/` both in Nginx and PHP-FPM containers and, by default, Nginx serves all PHP files located at `../public/`. All paths are relative to the directory where this repo was cloned.  

For example, consider a typical PHP webapp having the following file structure:
```
.docker/
config/
public/
  index.php
  about.html   
src/
tmp/
vendor/
composer.json
composer.lock
``` 
where this repo was cloned in `.docker` directory. In this case, all files and folders alongside `.docker` are mounted into `/var/www/` directory in both Nginx and PHP-FPM containers, and Nginx serves files located at `public/`.
