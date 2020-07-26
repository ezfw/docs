---
title: "Error Handling"
date: 2020-07-06T22:35:39Z
draft: true
weight: 4
---

### Default Behaviour

By default EZFW will catch unhandled exceptions thrown in your application and return a 500 response to the user.

### Custom Error Handler

A custom error handler can be defined and used with EZFW to customize the response that is sent to the user. For example, changing the text sent:

```php
<?php

use EZFW\Http\ErrorHandler;
use Exception;

class TestErrorHandler extends ErrorHandler
{
    public function handle(Exception $e)
    {
        $response = parent::handle($e);
        return $response->text('Whoops! Something went wrong');
    }
}

$app->errorHandler(TestErrorHandler::class);
```