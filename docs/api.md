# API

Quarx's API is very simple, and it has a VERY simple auth system using a single token which can be defined with in your env. You can easily use this to manage integration with various platforms etc.
The general base route for all API requests is:

```
/quarx/api/{resource-url}?token={QUARX_API_TOKEN}
```

| URL | Resource |
| ------ | ----- |
| blog | Blog |
| events | Events |
| faqs | FAQs |
| files | Files |
| images | Images |
| pages | Pages |
| widgets | Widgets |

Each of these routes can be called or, you can also get a specific resource instance with the ID:

Example:
```
/quarx/api/blog/1?token=9a78sd6f9as6df9
```