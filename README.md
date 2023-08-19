# MOVIE_REVIEWS

django project

## App

Movie

In Django, the url template tag {% url 'signup' %} takes a URL pattern name – for example 'signup' – and returns a URL link.

```
...
<form action="{% url 'urlPatternName' %}">
        <div class="mb-3">
          <label for="email" class="form-label">
            Enter your email:
          </label>
...

...
urlpatterns = [
    path('curtomURL/', customView, name='urlPatternName'),
]
...

```
