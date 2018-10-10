---
title: 學習Django
date: 2018-07-31 00:30:19
tags:
---

Django
======

[Django Girls 教學](https://goo.gl/3Y28ed)
[Django Girls 學習指南](https://goo.gl/Nk7yVZ)
```shell=
mkdir djangogirls
cd djangogirls
```

```shell=
sudo apt-get install python-virtualenv
```

```shell=
virtualenv .vr
. .vr/bin/```activate
```

```shell=
pip install django
```

```shell=

django-admin.py startproject mysite .

```


```markdown=
ALLOWED_HOSTS = [
    "192.168.1.233"
]
```

```shell=
(myvenv) ~/djangogirls$ python manage.py runserver 0.0.0.0:8000

```

```shell=
(myvenv) ~/djangogirls$ python manage.py startapp blog
```

```python=
from django.db import models
from django.utils import timezone
from django.contrib.auth.models import User

class Post(models.Model):
    author = models.ForeignKey(User)
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(
            default=timezone.now)
    published_date = models.DateTimeField(
            blank=True, null=True)

    def publish(self):
        self.published_date = timezone.now()
        self.save()

    def __str__(self):
        return self.title
```

```shell=
 python manage.py makemigrations
```

```shell=
python manage.py syncdb
```





