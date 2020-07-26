---
title: "Getting Started"
date: 2020-07-06T22:06:32Z
---

## What is EZFW?

EZFW (easy framework) is a minimal and extensible PHP framework for building server side applications. EZFW is designed to be able to be run from a single file or to build entire applications.

## Installation

### Requirements

* PHP >= 7.4
* [Composer](https://getcomposer.org/)

### Installing EZFW

Create a new folder and then run the following commands from that folder:

```bash
composer init
composer require ezfw/ezfw
```

### Simple Example

First make an index.php file and add the following code:

```php
<?php

use EZFW\App;
use EZFW\Http\Request;
use EZFW\Http\Response;

require __DIR__ . '/vendor/autoload.php';

$app = App::boot();

$app->get('/', function (Request $request, Response $response) {
    return $response->text('Hello World');
});

$app->handle(Request::current());
```

Next run the following command to use the built-in PHP web server:

```bash
php -S localhost:8000
```

Finally navigate to [http://localhost:8000/](http://localhost:8000/) and you should see 'Hello World' displayed
