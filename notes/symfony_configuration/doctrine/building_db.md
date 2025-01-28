---
title: Bulding up the database
description: 
published: true
date: 2025-01-28T16:04:13.248Z
tags: db, doctrine, notes
editor: markdown
dateCreated: 2025-01-28T10:09:07.176Z
---

`composer require symfony/maker-bundle --dev`
`php bin/console make:entity`
`php bin/console make:migration`
`php bin/console doctrine:migrations:migrate`

`php bin/console make:controller ProductController`

`composer require --dev symfony/test-pack`
`php bin/phpunit`
`php bin/console make:controller ProductController`