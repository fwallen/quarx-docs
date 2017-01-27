# Publish

All custom modules will need to have their `Publishes` folder published in order to have their code added to you app. We've wrapped this into one simple command:

```
php artisan module:publish
```

Running this will place the files in the matching folders in your app. So if you want to have files put in migrations make sure your `Publishes` folder has a migration file in a directory like this:

```
Publishes/database/migrations/migration_file.php
```

If you switch themes in Quarx you will need to republish your module. The views are added directly into the themes.
