# php-nginx-composer-docker
Docker compose configuration in order to work in php + nginx

## Docker compose configuration
```
version: '3'
services:
    web:
        image: nginx:latest
        ports:
            - "8080:80"
        volumes:
            - ./app:/app
            - ./site.conf:/etc/nginx/conf.d/site.conf
            - ./logs:/var/log/nginx/
        links:
            - php
    
    php:
        image: 'php:7-fpm'
        volumes:
            - ./app:/app
```

## How to run
Previously, you need to install docker and docker compose. Please, go to the official site and install.

- https://docs.docker.com/install/
- https://docs.docker.com/compose/install/

When you finish, please run the next command inside the folder project.

```
docker-compose up
```
## Hello World with Composer

### Files

*app/composer.json*

```
{
    "name": "php-nginx-composer-docker",
    "require": {
        "rivsen/hello-world": "*"
    }
}
```

*app/index.php*
```
<?php
require_once "vendor/autoload.php";

$hello = new Rivsen\Demo\Hello();
echo $hello->hello();
```

### Install a dependency

Run the next command

```
docker run --rm -v $(pwd)/app:/app composer install
```

### Open in browser

http://php-docker.local:8080/
