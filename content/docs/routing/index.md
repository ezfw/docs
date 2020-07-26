---
title: "Routing"
date: 2020-07-06T22:32:19Z
weight: 2
---

### Available Methods

By default EZFW allows you to register routes with the following methods:

```php
<?php

$app->get($route, $handler)
$app->post($route, $handler)
$app->put($route, $handler)
$app->delete($route, $handler)
```

### Route Handlers

Route handlers can either be defined as a callable:

```php
<?php

use EZFW\Http\Request;
use EZFW\Http\Response;

$app->get('/myCallable', function (Request $request, Response $response) {
    return $response->text("Hello from my callable");
});
```

or an Action:

```php
<?php

use EZFW\Http\Action;
use EZFW\Http\Request;
use EZFW\Http\Response;

class MyAction extends Action {
    public function handle(Request $request, Response $response) : Response
    {
        return $response->text('Hello from my action');
    }
}

$app->get('/myAction', MyAction::class);
```

### Route Parameters

Route parameters can be used to capture part of a route URI as part of the request. Route parameters can be defined in a route URI by surrounding the name with `{}`. For example, if you wanted to capture a user ID in the URI:

```php
<?php

use EZFW\Http\Request;
use EZFW\Http\Response;

$app->get('/user/{userId}', function (Request $request, Response $response) {
    $value = $request->parameters['userId'];
    return $response->text("userId: {$userId}");
});
```