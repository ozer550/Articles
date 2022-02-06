# Django Url Resolvers

Django resolvers are utility functions which help us to resolve path and meta data of urls using the url name. As we know hard coding stuff is really bad as it becomes really hard to fix bugs, there maybe many instances where we have hardcoded a url and changing the main route of url in urls.py may brake your whole website and you may need to fix every instance of that hard coded url manually. This is where django url Resolver utilities come into play. They help us to resolve path of urls using there given url name, this way we need not to worry about the various instances of the url bieng used, we can just change it in the main urls.py file and every where else it will automatically resolve using utilities.

Consider the following urls.py cide for an app:

```
