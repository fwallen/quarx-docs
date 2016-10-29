# Introduction

Quarx comes with a handful of prebuilt modules for handling a basic application including Images, Files, Blog, Pages, Faqs, etc. Below you will find a full listing of the modules that come prepackaged with Quarx.

In order to create your own Modules and ensure that they are loaded you MUST add `"Quarx\\": "quarx/"` to the PSR-4 group in your `composer.json` file.

Pre-packaged Modules
------
* Blog
* Pages
* Menus
* Widgets
* Faqs
* Images
* Files
* Events

You have the freedom to make any modules you want. You can use the `artisan module:make` or the `artisan module:crud` to generate them and then `artisan module:publish` to publish their contents.
