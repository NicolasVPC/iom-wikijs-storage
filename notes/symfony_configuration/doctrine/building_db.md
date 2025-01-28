---
title: Bulding up the database
description: 
published: true
date: 2025-01-28T10:25:19.232Z
tags: db, doctrine, notes
editor: markdown
dateCreated: 2025-01-28T10:09:07.176Z
---

`composer require symfony/maker-bundle --dev`
`php bin/console make:entity`
`php bin/console make:migration`
`php bin/console doctrine:migrations:migrate`