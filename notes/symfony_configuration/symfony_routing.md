---
title: Symfony routing
description: 
published: true
date: 2025-01-26T09:28:44.202Z
tags: config, routing, symfony
editor: markdown
dateCreated: 2025-01-26T09:23:47.254Z
---

# How to configure routes
In Symfony there are two ways to configure routes for the API:
1. You add the following library: `Symfony\Component\Routing\Attribute\Route`, then you add `#Route('route/path', 'route_name']`
in the following example the route is `/foo/bar`:
``` php
<?php
// src/Controller/FooController.php
namespace App\Controller;

use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Attribute\Route;

class FooController
{
    #[Route('/foo/bar')]
    public function bar(): Response
    {
        $foo = "foo";

        return new Response(
            '<html><body>Foo: '.$foo.'</body></html>'
        );
    }
}
```
2. - Create a `config/routes/attributes.yaml` file:
``` yaml
# config/routes/attributes.yaml
controllers:
    resource:
        path: ../../src/Controller/
        namespace: App\Controller
    type: attribute

kernel:
    resource: App\Kernel
    type: attribute
```
- Create a `config/routes/routes.yaml` file:
``` yaml
# config/routes.yaml
blog_list:
    path: /foo/bar
    # the controller value has the format 'controller_class::method_name'
    controller: App\Controller\FooController::bar

    # if the action is implemented as the __invoke() method of the
    # controller class, you can skip the '::method_name' part:
    # controller: App\Controller\FooController
```

