### dump data
```bash
python manage.py dumpdata --exclude=auth --exclude=contenttypes > data.json
python manage.py dumpdata quiz > data.json
```

### load data
```bash
python manage.py loaddata data.json
```

# running tests in bloggin application
python manage.py test blogging

# starting a Django project
pip install Django
django-admin startproject mysite
cd mysite
python manage.py runserver
python manage.py migrate
python manage.py createsuperuser
python manage.py startapp polling
## Then add `polling` to INSTALLED_APPS in mysite/settings.py

# Running shell in python
py .\manage.py shell

# Example of listing all objects
all_users = User.object.all()

# Creating a super user
py .\manage.py createsuperuser

# create migration
py .\manage.py migrate

# new application in a solution - i new subfolder
django-admin startapp blog

# Run server allowing from anywhere
py manage.py runserver 0.0.0.0:8000

# start server
py manage.py runserver

# Start new project in Django, dot tells to create project in current folder
django-admin startproject algorymikastartproject 

# Install Django
pip install django

# shell examples
>>> a = Post.objects.all()  #<-- no query yet
>>> b = a.filter(title__icontains="post")  #<- not yet
>>> c = b.exclude(text__contains="created")  #<-- nope
>>> [(p.title, p.text) for p in c]  #<-- This will issue the query
>>> a.count()  #<-- immediately executes an SQL query
>>> [p.pk for p in Post.objects.all().order_by('created_date')]
    [1, 2, 3, 4]
>>> [p.pk for p in Post.objects.all().order_by('-created_date')]
    [4, 3, 2, 1]
>>> [p.pk for p in Post.objects.filter(title__contains='post')]
    [1, 2, 4]
>>> [p.pk for p in Post.objects.exclude(title__contains='post')]
    [3]
>>> qs = Post.objects.exclude(title__contains='post')
>>> qs = qs.exclude(id__exact=3)
>>> [p.pk for p in qs]
    []
>>> qs = Post.objects.exclude(title__contains='post', id__exact=3)
>>> [p.pk for p in qs]
    [1, 2, 3, 4]
>>> qs = Post.objects.all()
>>> [p.published_date for p in qs]
    [None, None, None, None]
>>> from datetime import datetime
>>> from django.utils import timezone
>>> now = timezone.now()
>>> qs.update(published_date=now)
    4
>>> [p.published_date for p in qs]

# If you are curious, you can see the SQL that a given QuerySet will use:
>>> print(c.query)
   SELECT "blogging_post"."id", "blogging_post"."title", "blogging_post"."text",
          "blogging_post"."author_id", "blogging_post"."created_date",
          "blogging_post"."modified_date", "blogging_post"."published_date"
   FROM "blogging_post"
   WHERE (
       "blogging_post"."title" LIKE %post% ESCAPE '\'
       AND NOT ("blogging_post"."text" LIKE %created% ESCAPE '\')
   )
  
### Connect to Azure SQL Database
  DATABASES = {
    'default': {
         'ENGINE': 'mssql',
         'Trusted_Connection': 'no', 
         'OPTIONS': { 
             'driver': 'ODBC Driver 17 for SQL Server', 
             'extra_params': "Authentication=ActiveDirectoryMsi;Encrypt=yes;TrustServerCertificate=no" }
     }
}
 
