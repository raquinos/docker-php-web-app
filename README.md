# docker-php-web-app
A Docker setup for running a PHP7 web app.

Exposes an Nginx web server that runs PHP scripts through PHP-FPM.

Each service (Nginx, PHP-FPM) is configured as a Docker container, following the approach presented in [this great tutorial](https://www.pascallandau.com/blog/php-php-fpm-and-nginx-on-docker-in-windows-10).

The `../` directory is mounted as a volume in `/var/www/` both in Nginx and PHP-FPM containers and, by default, Nginx serves all PHP files located at `../public/`. All paths are relative to the directory where this repo was cloned.  
