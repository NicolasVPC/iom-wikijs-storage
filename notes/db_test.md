---
title: Database test
description: 
published: true
date: 2025-01-26T10:59:26.540Z
tags: db, docker, notes, test
editor: markdown
dateCreated: 2025-01-26T10:57:51.993Z
---

# Set up the database for testing

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