---
title: Database test
description: 
published: true
date: 2025-01-26T11:01:53.546Z
tags: db, docker, notes, test
editor: markdown
dateCreated: 2025-01-26T10:57:51.993Z
---

# Set up the database for testing
The database will listen on the port `8087` and it is in the same network of `adminer`.
Here the `docker-compose.yaml` file for `db-test`:
``` yaml
services:
  db-test:
    image: mariadb:11.4
    restart: unless-stopped
    env_file:
      - db.env
    # environment:
      # MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}  # Set in .env
      # MYSQL_USER: ${MYSQL_USER}                    # Set in .env
      # MYSQL_PASSWORD: ${MYSQL_PASSWORD}            # Set in .env
    volumes:
      - ./data:/var/lib/mysql
      - ./scripts:/docker-entrypoint-initdb.d
    ports:
      - 8087:3306
    networks:
      - doc_development
    ulimits:
      memlock: "262144"

networks:
  doc_development:
    external: true
```

Here the `docker-compose.yaml` inside `doc/`:
``` yaml
services:
  iom-db:
    image: mariadb:11.4
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
    networks:
      - development

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

networks:
  development:
    driver: bridge
    driver_opts:
      com.docker.network.bridge.host_binding_ipv4: "127.0.0.1"

```

as you can see `development` is the common network.