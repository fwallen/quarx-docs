# Composer

So now you've made a Quarx module and it's serving your application well, but now you've decided that it would make more sense for it to be a composer package, that you can run inside any app for easier maintenance. This also gives you far more freedom to decide how you wish to integrate the module into your app.

```
module:composer {name} {namespace}
```

This will generate a composer file, as well set the namespace of your module to a new package namespace.

