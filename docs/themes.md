# Introduction

Quarx has a full scope theming tool built right in. You can easily generate basic themes that can be built on and kept clear of your views. All the listed templates with a star are optional - otherwise everything else is required, for the basic support.

Basic Theme Structure
------
* assets
    * js
        * theme.js
    * sass
        * _basic.scss <span class="fa fa-star"></span>
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

You have the ability to include other theme views into your view using the <code>&#64;theme('path')</code> directive with Blade. Otherwise its basically anything and everything Blade can do including any directives you wish to expand it with.
