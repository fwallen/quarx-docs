# Pages and Blocks

There are some special features for pages which are not available for other parts of the site.

### Blocks

Pages are special and can often require complex designs. If your application needs some of the more abstract designs you can still use Quarx for page management by using the block system.

```php
{!! $page->block('main') !!}
```

By placing code like this in your template Quarx will generate the `main` block if it does not exist yet. If it does and has content it will render the content. It's really that simple.
