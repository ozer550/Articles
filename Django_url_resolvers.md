# Django Url Resolvers

Django resolvers are utility functions which help us to resolve path and meta data of urls using the url name. As we know hard coding stuff is really bad as it becomes really hard to fix bugs, there maybe many instances where we have hardcoded a url and changing the main route of url in urls.py may brake your whole website and you may need to fix every instance of that hard coded url manually. This is where django url Resolver utilities come into play. They help us to resolve path of urls using there given url name, this way we need not to worry about the various instances of the url bieng used, we can just change it in the main urls.py file and every where else it will automatically resolve using utilities.

Consider the following urls.py code for an app:

```python
from django.urls import path
from .views import ProjectsListView , ProjectCreateView , ProjectDetailView

urlpatterns = [
    path('/projects', ProjectsListView.as_view(), name='home'),
]
```

Here we have defined a url pattern with its corresponding url name. Now consider the view for following route:

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

If we carefully see here we have defined a url attribute for ProjecctsListView class and we have hard coded the string.

```python
 url = '/projects'
```

Now for some reasons we change the main route in urls.py to the following:

```python
 path('/proj', ProjectsListView.as_view(), name='home'),
```
clearly this will brake the url attribute that we hardcoded in the ProjectListView class. To avoid this we can use the utilitiy functions in as follows:

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
This is a utility function which spits out string object which has the url path. What it means is that it spits out string with a value of the path of the url, so if we use reverse on home url name in above example i.e 
```python
reverse('home')
```
 it will spit out:

```python
'/proj' as result.
```

## reverse_lazy()
This function is best defined by the official Django docs as "A lazily evaluated version of reverse()". If properly used this will also give the same result returning the path to the corresponding url name, but this function returns an object and evaluates only when it is required and hence called lazy.




 

