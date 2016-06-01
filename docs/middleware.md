# Middleware

Quarx adds one key middleware to your application. This can be set with whatever rules you wish to apply to the CMS. For example you may wish to have only _admin_ level users use the CMS so you can set those rules in the `handler` of the Quarx middleware.

## Quarx
The Quarx middleware is a requirement to all quarx routes.

```
['middleware' => 'quarx']
```

## Quarx Access

Quarx requires Laracogs to run (mostly for the FormMaker), but Laracogs does not require you to use its version of roles. But you will still need to ensure some degree of control for Quarx's access. A suggested approach to handling Quarx access:

Possible Quarx Policy:
```
$gate->define('quarx', function ($user) {
    return ($user->roles->first()->name === 'admin');
});
```

Quarx Middleware Handler:
```
public function handle($request, Closure $next)
{
    if (Gate::allows('quarx')) {
        return $next($request);
    }

    return response('Unauthorized.', 401);
}
```