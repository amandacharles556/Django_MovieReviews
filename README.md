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
