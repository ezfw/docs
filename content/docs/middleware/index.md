---
title: "Middleware"
date: 2020-07-06T22:35:26Z
draft: true
weight: 3
---

### Available Methods

By default EZFW allows you to register middleware with the following methods:

```php
<?php

$app->before($middleware)
$app->after($middleware)
```

Middleware can either be run before the route is handled, using the before method, or after, using the after method. This allows responses to be modified at any part of the lifecycle.

### Registering middleware

Middleware can be defined as either a callable:

```php
<?php

use EZFW\Http\Request;
use EZFW\Http\Response;

$app->before(function (Request $request, Response $response, callable $next) {
    $response->addHeader('test', 'true');
    $next($request, $response);
});
```

or a Middleware class:

```php
<?php

use EZFW\Http\Middleware;
use EZFW\Http\Request;
use EZFW\Http\Response;

class MyMiddleware extends Middleware
{
    public function handle(Request $request, Response $response, callable $next)
    {
        $response->addHeader('test', 'true');
        $next($request, $response);
    }
}


$app->before(MyMiddleware::class);
```