# Blade Directives

Quarx has some custom directives added to Blade which allows you to include files from your theme easily, as well as other parts.

### &#64;theme('path.to.view')
You can always add the <code>quarx-frontend::</code> namespace to the <code>&#64;include('path')</code> or instead use <code>&#64;theme('path')</code>.

### &#64;block('slug')

Create unique and elegant designs with block directives in your templates for pages.

### &#64;menu('slug')

Easily add menus to your views with the menu blade directive.

### &#64;widget('slug')

Add widgets to your views with the menu blade directive, just specify the SLUG.

### &#64;image('id', 'class')

Provides an image URL with an html tag and extra for adding a class

### &#64;image_link('ID')

Provides an image URL

### &#64;images('tag')

Images will be provided as an array, and if you skip the tag then the method will return all images, otherwise it follows the tagging.

### &#64;edit('module', 'id')

There is also the Quarx Service which can be run inside your blade views. Its as simple as {{ Quarx::method() }}

Helper Methods Available:
------
* menu('slug', 'optional-view-path')
* images('tag')
* widget('slug')
* editBtn('module', 'id')
