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

## Connecting to MySQL Database

first, create database `moviereviews` using `xampp/phpMyAdmin`

second, apply some changes

```
pip install pymysql
pip install mysqlclient
```

```moviereviews/__init__.py
  import pymysql
  pymysql.install_as_MySQLdb()
```

```moviereviews/setting.py
  DATABASES = {
    'default': {
      'ENGINE': 'django.db.backends.mysql',
      'NAME': 'moviereviews',
      'USER': 'root',
      'PASSWORD': '',
      'HOST':'localhost',
      'PORT':'3306',
    }
  }
```

third, `py manage.py makemigrations`, `py manage.py migrate`

## Add base.html

Alter `settings.py`

```
TEMPLATES = [
  {
    'BACKEND': 'django.template.backends.django.DjangoTemplates',
    'DIRS': [os.path.join(BASE_DIR, 'moviereviews/templates')],
    'APP_DIRS': True,
    'OPTIONS': {
      'context_processors': [
        'django.template.context_processors.debug',
        'django.template.context_processors.request',
        'django.contrib.auth.context_processors.auth',
        'django.contrib.messages.context_processors.messages',
      ],
    },
  },
]
```

## create `base.html`

```
<!DOCTYPE html>
<html>
  <head>
  ...
  </head>

  <body>
  ...
  {% block content %} {% endblock content %}
  ...
  </body>
</html>

```

To use this `base.html`,

```
{% extends 'base.html' %}
{% block content %}
...
{% endblock content %}
```

## Serving static files

settings.py:

```
…
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/4.0/howto/static-files/
STATIC_URL = 'static/'
…
```

add this,

```
...
STATICFILES_DIRS = [
  BASE_DIR/'.../static/',
]
...
```

page.html:
add this `{% load static %}` in corresponding position

## Implementing User Signup and Login

### Creating a signup form

```
  from django.contrib.auth.forms import UserCreationForm
```

### Creating a user

```
  from django.contrib.auth.models import User
  from django.contrib.auth import login
```

### Handling user creation errors

```
  from django.db import IntegrityError
```

### Customizing UserCreationForm

```
  class UserCreateForm(UserCreationForm):
    def __init__(self, *args, **kwargs):
      super(UserCreateForm, self).__init__(*args, **kwargs)
```

### Showing whether a user is logged in

```
  {% if user.is_authenticated %}
    <a class="nav-link" href="#">
      Logout ({{ user.username }})
    </a>
  {% else %}
    ...
  {% endif %}
```

### Implementing the logout functionality

```
  from django.contrib.auth import logout
  def logoutaccount(request):
    logout(request)
    return redirect('home')
```

### Implementing the login functionality

```
  from django.contrib.auth.forms import AuthenticationForm
  from django.contrib.auth import authenticate
```

# Letting Users Create, Read, Update, and Delete Movie Reviews

### Creating a review

### Listing reviews

### Updating a review

### Deleting a review

### Implementing authorization

```
from django.contrib.auth.decorators import login_required
…
@login_required
def func():
```
