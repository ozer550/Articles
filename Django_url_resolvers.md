# Django Url Resolvers

Django resolvers are utility functions that help us to resolve path and metadata of urls using the URL name. As we know hard coding stuff is really bad as it becomes really hard to fix bugs, there may be many instances where we have hardcoded a URL and changing the main route of URL in urls.py may brake your whole website and you will need to fix every instance of that hardcoded URL manually. This is where django url resolver utilities come into play. They help us to resolve path of urls using their given URL name, this way we need not worry about the various instances of the URL being used, we can just change it in the main urls.py file, and everywhere else it will automatically resolve using utilities.

Consider the following urls.py code for an app:

```python
from django.urls import path
from .views import ProjectsListView , ProjectCreateView , ProjectDetailView

urlpatterns = [
    path('/projects', ProjectsListView.as_view(), name='home'),
]
```

Here we have defined a URL pattern with its corresponding URL name. Now consider the view for the following route:

```python
from django.shortcuts import render
from django.views.generic import ListView, DetailView, CreateView, UpdateView, DeleteView
from django.urls import reverse, reverse_lazy


from .models import Projects
# Create your views here.

class ProjectsListView(ListView):
    model = Projects
    url = '/projects'
    template_name = 'projects_list.html'
```

If we carefully see here we have defined a url attribute for ProjecctsListView class and we have hardcoded the string.

```python
 url = '/projects'
```

Now for some reasons we change the main route in urls.py to the following:

```python
 path('/proj', ProjectsListView.as_view(), name='home'),
```
clearly, this will break the url attribute that we hardcoded in the ProjectListView class. To avoid this we can use the utility functions in as follows:

```python
from django.shortcuts import render
from django.views.generic import ListView, DetailView, CreateView, UpdateView, DeleteView
from django.urls import reverse, reverse_lazy


from .models import Projects
# Create your views here.

class ProjectsListView(ListView):
    model = Projects
    url = reverse_lazy('home');
    template_name = 'projects_list.html'
```
This way we just provide the url name to the reverse_lazy function and it automatically spits out the correct url for the url attribute. The two commonly used url resolver functions are:
- reverse( )
- reverse_lazy( )

## reverse( )
This is a utility function that spits out a string object which has the url path. What it means is that it spits out the string with a value of the path of the url, so if we use reverse on home url name in above example i.e 
```python
reverse('home')
```
 it will spit out:

```python
'/proj' as result.
```

## reverse_lazy()
This function is best defined by the official Django docs as "A lazily evaluated version of reverse()". If properly used this will also give the same result returning the path to the corresponding url name, but this function returns an object and evaluates only when it is required and hence called lazy.
