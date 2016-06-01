# Update

Regarding updates
-----
From time to time we may do updates to Quarx that can cause involve breaking changes. We would like to explain the two main ways of handling the updates that occur in Quarx. We will specify if there are migrations to do be done inside the Release notes for each release.

## Migrations
If there are migrations that need to happen, all you need to do is run:

```
php artisan vendor:publish --provider="Yab\Quarx\QuarxProvider"
```

Which will publish all the missing migrations. Then you can run the actual migration:

```
php artisan migrate
```

## Composer

The other option is composer lock. Rather than do your releases off the composer.json you could set them to run off the composer.lock. Alternative to that you could simply lock the version number in your composer file. Which will prevent the core of Quarx from changing.
