---
title: Symfony configuration
description: 
published: true
date: 2025-01-29T14:31:53.214Z
tags: config, docker, notes, symfony
editor: markdown
dateCreated: 2025-01-24T18:37:41.173Z
---

# Set up a symfony project in Docker
## Installing & Setting up the Symfony Framework
src: https://symfony.com/doc/current/setup/docker.html
According to the guidelines of symfony documentation there are two supported ways to run symfony projects through docker:
- The Complete Docker Environment; it's an environment where PHP, web server, database, etc. are all in docker. https://github.com/dunglas/symfony-docker 
- The symfony binary docker integration; It's necessary to install PHP on your own local machine
---

Installing the [Symfony CLI](https://symfony.com/download) and running `symfony check:requirements`, we encountered the following problems:

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

### create the project
``` bash
# run this if you are building a traditional web application
symfony new my_project_directory --version="7.2.x" --webapp

# run this if you are building a microservice, console application or API
symfony new my_project_directory --version="7.2.x"
```

In this case Iliad Order Manager is an API, so: `symfony new api --version="7.2.2"`
version `7.2` end of support: July 2025 (https://symfony.com/releases/7.2)

running `cd api` then `symfony server:start` will run the server, and it will show up the symfony default homepage.

## dockerize the project
It's also possible to use Symfony Docker with existing projects!

First, [download this skeleton](https://github.com/dunglas/symfony-docker).

If you cloned the Git repository, be sure to not copy the `.git` directory to prevent conflicts with the `.git` directory already in your existing project.
You can copy the contents of the repository using git and tar. This will not contain `.git` or any uncommited changes.

    git archive --format=tar HEAD | tar -xC my-existing-project/

If you downloaded the skeleton as a zip you can just copy the extracted files:

    cp -Rp symfony-docker/. my-existing-project/

Enable the Docker support of Symfony Flex:

    composer config --json extra.symfony.docker 'true'

Re-execute the recipes to update the Docker-related files according to the packages you use

    rm symfony.lock
    composer recipes:install --force --verbose

Double-check the changes, revert the changes that you don't want to keep:

    git diff
    ...

Build the Docker images:

    docker compose build --no-cache --pull

Start the project!

    docker compose up -d

Browse `https://localhost`, your Docker configuration is ready!

This page means everything is working correctly:
![default-symfony7-homepage.png](/notes/default-symfony7-homepage.png)