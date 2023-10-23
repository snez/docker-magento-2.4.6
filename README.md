# Simple docker environment for Magento Open Source 2.4.6

## About

This is a super simple docker compose which sets up the absolute minimum environment dependencies for a Magento 2.4.6 installation.

- Designed as a base to be extended for other purposes.
- Not designed for production. Does not set up SSL on nginx or OpenSearch. Does not set up SMTP.
- This repository will not support other Magento versions, only Magento 2.4.6.

The environment consists of:
- PHP 8.2 and composer v2
- nginx 1.24
- mysql 8.0
- OpenSearch 2.5.0

The Magento root is by default under ./src. You can change this from .env.

Data from MySQL and OpenSearch will be persisted under ./data. Can be changed in .env.

Only the nginx port 80 is exposed to the host. Stop your web server before starting this one.

## Configuration files

The project sets basic defaults without making assumptions about your preferences. Please review and update the following files directly:

    .env
    php/auth.json
    php/php.ini
    nginx/settings.conf

## Start the services

    docker-compose up -d

## Install Magento

The image does not install Magento by default, you need to manually install it with:

    docker exec magento246_php install-magento

This will execute the script under ./php/install-magento.sh inside the php container.

## Access a shell

    docker exec -it magento246_php bash

composer v2 is available in the container for use.

## MacOS users

Make sure to enable virtiofs for performance

https://www.docker.com/blog/speed-boost-achievement-unlocked-on-docker-desktop-4-6-for-mac/