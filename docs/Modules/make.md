# Make

Quarx has a powerful CRUD builder. But lets say you want to have a custom module that integrates with another service or doesn't involve a CRUD at all. Then the `php artisan module:make` command will be your best tool. It will create a minimum viable module with a very basic admin layer and client layer. You can customize as you see fit.

## Redactor
You can utilize redactor in your module by adding `.redactor` to any textarea class.

## Images and Files:
Inside the redactor instance you can easily add images and files which you have uploaded to Quarx. Its as easy as clicking them to have them added to the entry.

## Front-end/ Theme
When you generate a module the system will also generate a front-end or theme component which is kept in the `Publishes` directory. The is the portion of code that your visitors will see. You will need to publish this code using the `php artisan module:publish {name}` command.
