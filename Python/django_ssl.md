### Use Django in ssl mode
1. pip install django-extensions Werkzeug pyOpenSSL
2. INSTALLED_APPS = (
    ...
    'django_extensions',
    ...
   )
3. python manage.py runserver_plus --cert /tmp/cert  0.0.0.0:8000
4. This will create a cert file at /tmp/cert.crt and a key file at /tmp/cert.key which can then be reused for future sessions.

### Run ssl Django application
python manage.py runserver_plus --cert /tmp/cert 0.0.0.0:8000
