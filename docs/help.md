# Help

Published Assets
-----
Quarx publishes views and controllers within your application. This allows you to control everything you want. You will find the controllers in: `app/Http/Controllers/Quarx` and the views in: `resources/views/quarx`. There is also the quarx config which is added to your app's config directory.

Quarx will also be able to generate cutom modules which you can find in the following directory: `quarx/modules`
To generate these files simple run:

```
php artisan vendor:publish
```

Front-End Code
-----
Quarx automatically builds you a sample of the controllers, and views for your application's pages, blog, faqs, etc. There are two main method calls available outside of the standard Laravel methods:

```
Quarx::widget('slug') // Renders the widget
```

and

```
Quarx::menu('slug', 'css-class') // Renders the menu
```

These can be used in various ways. The menu can also have a class added to it for easier rendering.