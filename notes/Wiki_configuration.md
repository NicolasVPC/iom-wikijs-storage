---
title: Wiki.js configuration
description: 
published: true
date: 2025-01-23T20:04:42.097Z
tags: notes, wikijs, config
editor: markdown
dateCreated: 2025-01-23T20:04:42.097Z
---

# Introduction
Here you can find how to setup the Wiki.js software, here the official website of Wiki.js: https://js.wiki/ 
Docker setup: https://docs.requarks.io/install/docker

# Setup

``` yaml
services:
  iom-db:
    image: mariadb:11.2
    restart: unless-stopped
    env_file:
      - db.env
    # environment:
      # MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}  # Set in .env
      # MYSQL_DATABASE: ${MYSQL_DATABASE}            # Set in .env
      # MYSQL_USER: ${MYSQL_USER}                    # Set in .env
      # MYSQL_PASSWORD: ${MYSQL_PASSWORD}            # Set in .env
    volumes:
      - ./data:/var/lib/mysql
    ports:
      - 8085:3306
      
  iom-adminer:
    image: adminer
    restart: unless-stopped
    ports:
      - 8083:8080

  iom-wiki:
    image: ghcr.io/requarks/wiki:2.5.305
    restart: unless-stopped
    depends_on:
      - iom-db
    env_file:
      - wiki.env
    environment:
      DB_HOST: iom-db
      DB_TYPE: mariadb
      DB_PORT: 3306
      # ADMIN_EMAIL: ${ADMIN_EMAIL}
      # ADMIN_PASS: ${ADMIN_PASS}
      # DB_USER: ${DB_USER}
      # DB_PASS: ${DB_PASS}
      # DB_NAME: ${DB_NAME}
    ports:
      - 8084:3000

```