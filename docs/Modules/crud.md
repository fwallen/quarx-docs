# CRUD

Quarx can generate custom CRUD modules for your application giving it all the power you want as fast as possble. There are many hidden powers inside Quarx, you can discover them by reading below.
The CRUD generator will produce a module with basic unit tests started. You would then need to setup your migrations etc, and then publish the module to your app. Check out the publishing for more details.

## Forms
You can use the Form Maker tool which is provided by [Laracogs](https://laracogs.com)

## Redactor
You can utilize redactor in your CRUD by adding `.redactor` to any textarea class.

## Images and Files:
Inside the redactor instance you can easily add images and files which you have uploaded to Quarx. Its as easy as clicking them to have them added to the entry.

## Front-end/ Theme
When you generate a module the system will also generate a front-end or theme component which is kept in the `Publishes` directory. The is the portion of code that your visitors will see. You will need to publish this code using the `php artisan module:publish {name}` command.
