# reverse vs reverse_lazy
A deep question that arises when thinking about these two url resolver functions is when to use what and why we need these two if both of them almost do the same thing.

## Need of reverse_lazy( )
We need reverse-lazy( )  as there may arise a condition in the workflow in which the url configurations are not fully loaded and we may try to access some information about them. Consider the following urls.py and views.py files for an app:


```python
#urls.py
from django.urls import path
from .views import ProjectDetailView

urlpatterns = [
    path('project/<int:pk>/', ProjectDetailView.as_view(), name='project_detail'),
]

```python
#views.py
from django.shortcuts import render
from django.views.generic import ListView, DetailView, CreateView, UpdateView, DeleteView
from django.urls import reverse_lazy

from .models import Projects


class ProjectDetailView(DetailView):
    model = Projects
    url = reverse('project_detail')
    template_name = 'project_detail.html'

```
If we look into the urls.py file we are importing ProjectDetailView class based view

```python
from .views import ProjectDetailView
```

Now there is a kick in here, every time we import a class its attributes get evaluated which means that the reverse function in the ProjectDetailView will get evaluated and will want to spit out the url for the desired url name, but as the url pattern is not even defined it will throw an error this is where reverse_lazy( ) can help as its lazy and would wait for urlconf to get fully loaded.

Therefore we need to use reverse_lazy in the following conditions as stated by official docs:
- providing a reversed URL as the url attribute of a generic class-based view.
- providing a reversed URL to a decorator (such as the login_url argument for the django.contrib.auth.decorators.permission_required() decorator).
- providing a reversed URL as a default value for a parameter in a function’s signature.
