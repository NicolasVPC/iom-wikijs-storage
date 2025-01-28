---
title: Doctrine
description: 
published: true
date: 2025-01-28T09:13:17.262Z
tags: db, doctrine, notes
editor: markdown
dateCreated: 2025-01-27T18:04:14.422Z
---

# First steps with Doctrine
https://symfony.com/doc/current/doctrine.html
https://symfony.com/doc/6.4/the-fast-track/en/8-doctrine.html
https://symfonycasts.com/screencast/symfony-doctrine/docker-compose
vedi also documentazione locale

The `orm` Symfony pack is needed in order to configure Doctrine and create the db:
``` bash
composer require symfony/orm-pack
composer require --dev symfony/maker-bundle
```
inside the `.env` file in `app/` you have to set up the `DATABASE_URL` env variable, we will use mysql:
``` env
# app/.env
MYSQL_ROOT_PASSWORD=securepassword
MYSQL_USER=tester
MYSQL_PASSWORD=securepassword
MYSQL_DATABASE=app
DATABASE_URL=mysql://${MYSQL_USER:-tester}:${MYSQL_PASSWORD:-pS5fqZ8pUN3yrAs}@database:3306/${MYSQL_DATABASE:-app}?serverVersion=${MYSQL_VERSION:-8.4}&charset=${MYSQL_CHARSET:-utf8mb4}
```
