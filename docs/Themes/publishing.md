# Publishing

## Command
```
php artisan theme:publish {name}
```

The Quarx theme publisher will publish the public directory only. If you want to integrate assets you need to do so using your `webpack` or `gulp` file, pending on which setup you use.

| Laravel Verison | Asset builder |
| --- | --- |
| 5.4 | `webpack.mix.js` |
| 5.3 | `gulpfile.js` |

Basic Theme
------
* assets
    * js
        * theme.js
    * sass
        * _basic.scss
        * _theme.scss
* blog
    * all.blade.php
    * featured-template.blade.php
    * show.blade.php
* events
    * all.blade.php
    * date.blade.php
    * calendar.blade.php
    * featured-template.blade.php
    * show.blade.php
* faqs
    * all.blade.php
* gallery
    * all.blade.php
    * show.blade.php
* layout
    * master.blade.php
* pages
    * all.blade.php
    * featured-template.blade.php
    * home.blade.php
    * show.blade.php
* partials
    * navigation.blade.php
* public
    * img

