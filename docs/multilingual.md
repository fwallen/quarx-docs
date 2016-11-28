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
