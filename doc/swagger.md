# DRF_01 

setting편에 이어서 

- swagger와 


### install
[drf-swagger-설치](https://django-rest-swagger.readthedocs.io/en/latest/)

```
$ pip install django-rest-swagger

settings.py

INSTALLED_APPS = [
    ...
    'rest_framework_swagger',
    ...
]

```


urls.py 

```
from django.conf.urls import url
from rest_framework_swagger.views import get_swagger_view

schema_view = get_swagger_view(title='Pastebin API')

urlpatterns = [
    ...,
    url('doc/', schema_view)
]

```