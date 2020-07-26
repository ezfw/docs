---
title: "Plugins"
date: 2020-07-06T22:35:32Z
draft: true
weight: 6
---

Plugins are a simple way to collect related functionality like registering routes, middleware etc. in one place.

### Using Plugins

```php
<?php

use EZFW\App;
use EZFW\Http\Plugin;
use EZFW\Http\Request;
use EZFW\Http\Response;

class MyPlugin extends Plugin
{
    public function boot(App $app, array $config)
    {
        $app->get('/myPlugin', function (Request $request, Response $response) {
            return $response->text('Hello from my plugin');
        });
    }
}}

$app->use(MyPlugin::class);
```