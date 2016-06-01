# Welcome to Quarx

Quarx is a CMS for Laravel applications. It provides numerous components that enable developers to put together powerful applications but also provide the means for people to edit the content of those powerful applications.

Quarx comes with a module builder for all your custom CMS needs, as well as a module migration and publishing tools. So if you decide to reuse some modules on future projects you can easily publish thier assets seamlessly. If you wish to make your Quarx module into a PHP package, then you will need to have it publish its assets to the `quarx/modules` directory.

<div class="row text-center buttons">
    <a class="github-button" href="https://github.com/YABhq/Quarx" data-icon="octicon-star" data-style="mega" data-count-href="/YABhq/Quarx/stargazers" data-count-api="/repos/YABhq/Quarx#stargazers_count" data-count-aria-label="# stargazers on GitHub" aria-label="Star YABhq/Quarx on GitHub">Star</a>

    <a class="github-button" href="https://github.com/YABhq/Quarx/fork" data-icon="octicon-repo-forked" data-style="mega" data-count-href="/YABhq/Quarx/network" data-count-api="/repos/YABhq/Quarx#forks_count" data-count-aria-label="# forks on GitHub" aria-label="Fork YABhq/Quarx on GitHub">Fork</a>

    <a class="github-button" href="https://github.com/YABhq/Quarx/issues" data-icon="octicon-issue-opened" data-style="mega" data-count-api="/repos/YABhq/Quarx#open_issues_count" data-count-aria-label="# issues on GitHub" aria-label="Issue YABhq/Quarx on GitHub">Issue</a>
</div>

<div class="row">
    <div class="well text-center">
        <span><a href="https://yabhq.com">A Yab Inc. Product</a></span>
    </div>
</div>

<div class="row">
    <div class="col-md-6">
        <a data-toggle="lightbox" id="lightbox1" href="http://quarx.info/images/1.jpg">
            <img class="img-responsive thumbnail" alt="Screen 1" src="http://quarx.info/images/1.jpg" />
        </a>
        <a data-toggle="lightbox" id="lightbox2" href="http://quarx.info/images/2.jpg">
            <img class="img-responsive thumbnail" alt="Screen 2" src="http://quarx.info/images/2.jpg" />
        </a>
    </div>
    <div class="col-md-6">
        <a data-toggle="lightbox" id="lightbox3" href="http://quarx.info/images/3.jpg">
            <img class="img-responsive thumbnail" alt="Screen 3" src="http://quarx.info/images/3.jpg" />
        </a>
        <a data-toggle="lightbox" id="lightbox4" href="http://quarx.info/images/4.jpg">
            <img class="img-responsive thumbnail" alt="Screen 4" src="http://quarx.info/images/4.jpg" />
        </a>
    </div>
</div>

Installation
------

* Run the following command:

```bash
composer require yab/quarx
```

* Add the following to your Providers:

```php
Yab\Quarx\QuarxProvider::class
```

* Then run the vendor publish:

```bash
php artisan vendor:publish --provider="Yab\Quarx\QuarxProvider"
```

* Then migrate:

```bash
php artisan migrate
```

* Then add to the Kernal:

```php
'quarx' => [
    \App\Http\Middleware\Quarx::class,
],
```

* For Modules
In order to have modules load as well please add the following to your composer file:
```php
"Quarx\\": "quarx/",
```
This should be added to the autoloader below the App itself.

## Quarx Access

Quarx requires Laracogs to run (only for the FormMaker), but Laracogs does not require you to use its version of roles. But you will still need to ensure some degree of control for Quarx's access. This is done in the Quarx Middleware. If you opt in to the roles system provided by Laracogs, then you can use the logic below in your Quarx Middleware, if not, you will need to set your own security parameters for access to Quarx. To do this simply edit the Quarx middleware, and ensure that any rules you wish it to use are in the `handler` method. We suggest a policy similar to the following:

Possible Quarx Policy:
```
$gate->define('quarx', function ($user) {
    return ($user->roles->first()->name === 'admin');
});
```

Quarx Middleware Handler:
```
public function handle($request, Closure $next)
{
    if (Gate::allows('quarx')) {
        return $next($request);
    }

    return response('Unauthorized.', 401);
}
```

Also Provides
------
The Quarx package also provides the DevFactory Minify commands.

<script async defer id="github-bjs" src="https://buttons.github.io/buttons.js"></script>

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-39444410-3', 'auto');
  ga('send', 'pageview');

</script>
