---
title: Symfony routing
description: 
published: true
date: 2025-01-26T09:23:47.254Z
tags: config, symfony, routing
editor: markdown
dateCreated: 2025-01-26T09:23:47.254Z
---

# How to configure routes
In Symfony there are two ways to configure routes for the API:
1. You add the following library: `Symfony\Component\Routing\Attribute\Route`:
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