# Commands

## Quarx

Quarx comes with a few console commands to handle things like migrations and module building should you wish to expand your CMS.

Modules
------

The commmand for generating custom modules for Quarx is:

```
php artisan quarx:module {name} {--migration} {--schema="id:increments,name:string"}
```

The migration option will generate a migration file that can be found in the module. You will then need to run the module migrate to get the module to run its migration course.

Publish
------

Quarx also lets you publish assets that belong to a module. So in the chance you wish to build your own modules for future projects you can easily publish specific assets to any applications you build.

```
php artisan quarx:publish {module}
```

Prepare
------

If you opt in to use Quarx alongside Laracogs and use the Laracogs starter kit. Then Quarx can provide you with a skin to match your user settings, logins etc with Quarx. Allowing you develop what you want to faster.

```
php artisan quarx:prepare
```

## Theme

Quarx comes with a wonderfully simple theming component. Looking to generate a basic template - and build some custom ones? Then look no further.

Generate
------

Run the following command to generate a theme template:

```
php artisan theme:generate {name}
```

The theme's template will be generated using the name as its root folder. The theme can then easily be integrated into your site/ app by setting it in the Quarx config.

Publish
------

Some themes may have assets that need to be published for general access. Simply run the following command and you will have the theme's public folder published to your app's public folder.

```
php artisan quarx:publish {name}
```

