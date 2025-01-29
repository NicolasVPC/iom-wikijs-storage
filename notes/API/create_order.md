---
title: Create order API
description: 
published: true
date: 2025-01-29T10:49:55.161Z
tags: api
editor: markdown
dateCreated: 2025-01-28T16:12:00.646Z
---

# how to use the API
To add an order to the system, make a POST request to `/create/order` with a json file with the following parameters:
- name: string - **required**
- description: string - **optional**
- date: Date - **required**
- products: array of int - **required**

the API will create an entry with the specified parameters inside the `order` table and an entry inside `order_product` table to link the order to the wanted products.