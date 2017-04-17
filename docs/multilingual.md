# Multilingual

Translations
-----
All too often we need translations in our sites and even our apps. Quarx has got a very simple way of handling multiple languages. Trnaslations is set up so that in the config if you add any languages to the `languages` array you will be able to define custom entries for those languages.

#### Auto-Translate

```php
auto-translate: false
```

In order to enable the auto-translate ensure that it is set to true in your config.

## Translatable Modules

Simply add the translatable trait to your module's model and then update your modules to follow a similar pattern to the Quarx pages structure see the following files for reference:

```
Yab\Quarx\Controllers\PagesController
Yab\Quarx\Repositories\PageRepository
Yab\Quarx\Models\Page
```

#### Archiving and Clean up:

You will need to extend `QuarxModel` rather than the default Model. It will also need to use the `Translatable` Trait.

```
use Yab\Quarx\Models\QuarxModel;
use Yab\Quarx\Traits\Translatable;

class Books extends QuarxModel
{
    use Translatable;
}
```

You will also need to set bindings similar to this in your module event provider.

```
'eloquent.saved: Yab\Quarx\Models\Page' => [
    'Yab\Quarx\Models\Page@afterSaved',
],
'eloquent.created: Yab\Quarx\Models\Page' => [
    'Yab\Quarx\Models\Page@afterCreate',
],
'eloquent.deleting: Yab\Quarx\Models\Page' => [
    'Yab\Quarx\Models\Page@beingDeleted',
],
```

These bindings ensure that when you save you create an archive of the previous entry, and on deleting of a item the system clears out any translations and archives it left behind.
The created binding allows for the auto-translate so you can utilize the power of Google Translate.

## Supporting Language URL Prefixes

By default we support the use of cookies to handle languages and swapping them. Since each page/blog/event etc can have a specific url relative to its language with this current build there isn't much point to the prefixes for languages. But, that being said, sometimes its handy so here is an easy way to add support for it.

Just add this code to the `map()` method in the `RouteServiceProvider.php`:

```php
$segments = request()->segments();
$supportedLanguages = array_keys(config('quarx.languages'));

if (isset($segments[0]) && in_array($segments[0], $supportedLanguages)) {
    $language = $segments[0];
    unset($segments[0]);
    return redirect(implode('/', $segments))->withCookie('language', encrypt($language))->send();
}
```
