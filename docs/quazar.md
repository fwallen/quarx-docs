# Quazar

A remarkably simple e-commerce solution.

<img src="/img/quazar/screen-1.jpg" alt="">
<img src="/img/quazar/screen-2.jpg" alt="">

## Introduction

Obviously everyone likes to develop custom modules for their apps, and we all love the idea of selling stuff to make some extra cash on the side. Therefore, we're introducing Quazar. So you decided to start a blog or a website featuring your hobby or whatever, and now you're looking to make some sales. Simply pull in the Quazar package and within minutes you'll have a e-commerce platform up and running. Stylize it as much or as little as you want, set up some custom shipping and tracking number details, set your shipping rates and poof you've got a store.

Quazar is built in a way that allows for maximum customization with considerable simplicity in upgrading as time goes on. Initial publication will provide you with the controllers and a `StoreLogistics` service that you can hook your custom code into. The entire system is built using **Stripe** for very obvious reasons.

## Installation

```
composer require yab/quazar
composer require laravel/cashier
```

Don't worry about the laravel cashier installation, the only points of interest are specified below:

Add these to your `config/app.php`:

```
Yab\Quazar\QuazarModuleProvider::class,
Laravel\Cashier\CashierServiceProvider::class,
```

Add the following to your `app/Http/Kernel.php` to the `routeMiddleware` array:
```
'isAjax' => \Yab\Quazar\Middleware\isAjax::class,
```

Add the following to your `app/Providers/RouteServiceProvider.php` to the `mapWebRoutes` method inside the group method as a closure:
```
require base_path('routes/quazar.php');
```

Don't worry about the laravel cashier installation, the only points of interest are specified below:

Add the following to your `config/services.php`:

```php
'stripe' => [
    'model' => App\Models\UserMeta::class,
    'key' => env('STRIPE_KEY'),
    'secret' => env('STRIPE_SECRET'),
],
```

Now you need to add the Billable trait to the `App\Models\UserMeta::class`

```php
use \Laravel\Cashier\Billable;
```

Then publish the vendor assets etc:

```php
php artisan vendor:publish
php artisan migrate
```

If you wish to maintain consistency with the store accross your login, user settings etc you can set the extends to `@extends('quazar-frontend::layouts.store')`
Views you may wish to change for optimal consistency:

```
views/
    auth/
        login.blade.php
        register.blade.php
        passwords/
            email.blade.php
            reset.blade.php
    user/
        password.blade.php
        settings.blade.php
```

## Config

## Quarx & Laracogs
Quazar is intented to be used with Quarx so use outside of that context is to be done at your own risk. Similarly, though Quarx is able to be added to any existing Laravel 5.3+ application, the documentation above is in relation to using the `php artisan quarx:setup` command, which is heavily integrated with [Laracogs](https://laracogs.com).

#### CURRENCY
You can set the currency in the module `config.php` file. It is set to use an env setting `CURRENCY` but pending on your deployment this may not work correctly, and may need to be set manually.

## Customizing

Quazar is intented to be heavily customized per use. The general structure can support stores that sell digital and physical products, and integrate shipping management. But it can also be used to handle subscriptions. This means you can set up an instance of Quazar to handle subscriptions which produce orders which are shipped and tracked for your customers.

### LogisticService

The logistic service is published to your app specifically. The intention is for it to handle 'hooks' on the various events that occur within your store flow. The `LogisticService` handles the following events:

```php
shipping($user)
getTaxPercent($user)
afterPurchase($user, $transaction, $cart, $result)
afterSubscription($user, $plan)
afterRefundRequest($transaction)
afterRefund($transaction)
cancelSubscription($user, $plan)
afterPlaceOrder($user, $transaction, $cart)
orderCreated($order)
shipOrder($order)
cancelOrder($order)
```

### Routes & Controllers

There are a few controllers added to your app in the Quazar directory. These are general controllers which you may wish to customize based on your app's setup. This is similar to Quarx in the sense that you may wish to change certain parts. Be very mindful of how much you can impact the functionality of the Quazar store base by changing these files. Routes, however, are set in the package and the QuazarRoutesProvider handles them.

### Views

There are Quazar view files that are published your app which you can modify, however, if you wish to edit the package views then you will need to update them in the `resources/quazar` directory.

## Admin UI

There are some very easy to use Admin components set up with Quazar but feel free to clone the repo and add as you please. Here are some quick screenshots.

<img src="/img/quazar/screen-3.jpg" alt="">
<img src="/img/quazar/screen-4.jpg" alt="">
<img src="/img/quazar/screen-5.jpg" alt="">
<img src="/img/quazar/screen-6.jpg" alt="">