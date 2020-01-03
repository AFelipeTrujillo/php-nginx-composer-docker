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
    
    componser:
        image: 'composer'
```
