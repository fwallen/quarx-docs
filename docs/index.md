# Quarx Documentation

<div class="video-box">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/VVaryNGnXRM" frameborder="0"></iframe>
</div>

Quarx is a CMS for Laravel applications. It provides numerous components that enable developers to put together powerful applications but also provide the means for people to edit the content of those powerful applications.

Quarx comes with a module builder for all your custom CMS needs, as well as a module migration and publishing tools. So if you decide to reuse some modules on future projects you can easily publish thier assets seamlessly. If you wish to make your Quarx module into a PHP package, then you will need to have it publish its assets to the `quarx/modules` directory.

<div class="well text-center buttons">
    <a class="github-button" href="https://github.com/YABhq/Quarx" data-icon="octicon-star" data-style="mega" data-count-href="/YABhq/Quarx/stargazers" data-count-api="/repos/YABhq/Quarx#stargazers_count" data-count-aria-label="# stargazers on GitHub" aria-label="Star YABhq/Quarx on GitHub">Star</a>

    <a class="github-button" href="https://github.com/YABhq/Quarx/fork" data-icon="octicon-repo-forked" data-style="mega" data-count-href="/YABhq/Quarx/network" data-count-api="/repos/YABhq/Quarx#forks_count" data-count-aria-label="# forks on GitHub" aria-label="Fork YABhq/Quarx on GitHub">Fork</a>

    <a class="github-button" href="https://github.com/YABhq/Quarx/issues" data-icon="octicon-issue-opened" data-style="mega" data-count-href="/YABhq/Quarx/issues" data-count-api="/repos/YABhq/Quarx#open_issues_count" data-count-aria-label="# issues on GitHub" aria-label="Issue YABhq/Quarx on GitHub">Issue</a>
</div>

## Installation

Create a new Laravel application, and make a database somewhere and update the .env file.

* Run the following command:

```bash
composer require yab/quarx
```

* Add the following to your Providers:

```php
Yab\Quarx\QuarxProvider::class,
```

* Then run the vendor publish:

```bash
php artisan vendor:publish --provider="Yab\Quarx\QuarxProvider"
```

## Simple Setup

If you're looking to do a simple website with a powerful CMS, and the only people logging on to the app are the CMS managers. Then you can run the setup command.
Quarx will install everything it needs, run its migrations and give you a login to start with. Take control of your website in seconds.

```php
php artisan quarx:setup
```

Now your done setup. Login, and start building your amazing new website!

## Complex Setup

If you just want to add Quarx to your existing application and already have your own

* Add the following to your routes provider:

```php
require base_path('routes/quarx.php');
```

* Add the following to your app.scss file, you will want to modify depending on your theme of choice.

```css
@import "resources/themes/default/assets/sass/_theme.scss";
```

* Then migrate:

```bash
php artisan migrate
```

* Then add to the Kernel Route Middleware:

```php
'quarx' => \App\Http\Middleware\Quarx::class,
'quarx-api' => \App\Http\Middleware\QuarxApi::class,
```

In order to have modules load as well please edit the autoload psr-4 portion to your composer file:
```php
"autoload": {
    ...
    "psr-4": {
        "App\\": "app/",
        ...
        "Quarx\\": "quarx/"
        }
}
```

## Quarx Access
Route to the administration dashboard is "/quarx/dashboard".

Quarx requires Laracogs to run (only for the FormMaker), but Quarx does not require you to use the Laracogs version of roles. But you will still need to ensure some degree of control for Quarx's access. This is done in the Quarx Middleware, using the gate and the Quarx Policy. If you opt in to the roles system provided by Laracogs, then you can replace 'quarx' with admin to handle the Quarx authorization, if not, you will need to set your own security policy for access to Quarx. To do this simply add the Quarx policy to your `app/Providers/AuthServiceProvider.php` file, and ensure that any rules you wish it to use are in within the policy method. We suggest a policy similar to below.

Possible Quarx Policy:
```
Gate::define('quarx', function ($user) {
    return (bool) $user;
});
```

Or Using Laracogs:
```
Gate::define('quarx', function ($user) {
    return ($user->roles->first()->name === 'admin');
});
```

## API Endpoints

Quarx comes with a collection of handy API endpoints if you wish to use them. You can define your own policies for access and customize the middleware as you see fit.

#### Token

The basic Quarx API endpoints must carry the Quarx `apiToken` defined in the config for the app. This can be provided by adding the following to any request:

```
?token={your token}
```

** All published and public facing data will be available via the API by default.

```
/quarx/api/blog
/quarx/api/blog/{id}
/quarx/api/events
/quarx/api/events/{id}
/quarx/api/faqs
/quarx/api/faqs/{id}
/quarx/api/files
/quarx/api/files/{id}
/quarx/api/images
/quarx/api/images/{id}
/quarx/api/pages
/quarx/api/pages/{id}
/quarx/api/widgets
/quarx/api/widgets/{id}
```

Also Provides
------
The Quarx package also provides the following packages:

* DevFactory/Minify
* Yab/Laracogs

<script async defer id="github-bjs" src="https://buttons.github.io/buttons.js"></script>

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-39444410-3', 'auto');
  ga('send', 'pageview');

</script>
