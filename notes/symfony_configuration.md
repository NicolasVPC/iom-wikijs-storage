---
title: Symfony configuration
description: 
published: true
date: 2025-01-25T00:20:19.874Z
tags: config, docker, notes, symfony
editor: markdown
dateCreated: 2025-01-24T18:37:41.173Z
---

# Set up a symfony project in Docker
src: https://symfony.com/doc/current/setup/docker.html
According to the guidelines of symfony documentation there are two supported ways to run symfony projects through docker:
- The Complete Docker Environment; it's an environment where PHP, web server, database, etc. are all in docker. https://github.com/dunglas/symfony-docker 
- The symfony binary docker integration; è necessario aver installato PHP nella propria macchina locale.
---

Installing the [Symfony CLI](https://symfony.com/download) and running `symfony check:requirements` we encountered the following problems:

**no PHP binaries detected**
if the output is `no PHP binaries detected`, it means that you don't have php installed on the system, running `sudo apt install php-common libapache2-mod-php php-cli` will fix this issue.

**simplexml_import_dom() must be available**
this error means you must install SimpleXML extension.
``` bash                   
 [ERROR]                                          
 Your system is not ready to run Symfony projects 
                                                  

Fix the following mandatory requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 * simplexml_import_dom() must be available
   > Install and enable the SimpleXML extension.
```

Running: `sudo apt install php-xml` will fix the issue.

**Optional recommendations to improve your setup**
mb_strlen() should be available
Install and enable the mbstring extension.

intl extension should be available
Install and enable the intl extension (used for validators).

PDO should have some drivers installed (currently available: none)
Install PDO drivers (mandatory for `Doctrine`).
 
`sudo apt install php-mbstring php-intl php8.3-mysql`

appunti
/app/public/index.php
all'interno del container che viene creato in /app c'è il codice sorgente, sembra esserci l'associazione del volume ./:/app

