# check CLI version
heroku --version

# update CLI
heroku update

# create an application
heroku create

# check configuration
heroku config

# Push application to heroku
git init
heroku create
git remote -v
heroku config:set SECRET_KEY=k325354k3DGDFGDFG55432BDFDSS
pip install gunicorn psycopg2-binary
pip freeze > requirements.txt
## create a file named Procfile with: web: gunicorn main:app ##
echo "web: gunicorn main:app" > Procfile
git add .
git commit -a -m "Initial commit"    # Only necessary because this is a new git repo.
git push heroku master               # If you have any changes or files to add, commit them before you push. 
heroku addons:create heroku-postgresql:mini
heroku run python setup.py
heroku open

# Depolying Flask application
git init
heroku create
pip freeze > requirements
git remote -version
git add .
git commit -a -m "Initial commit"
git push heroku master
heroku open


# Setting variables
heroku create
heroku config:set DJANGO_SETTINGS_MODULE=heroku
heroku config:set SECRET_KEY=NnUdYr28vxncCAuYyppNp33H
heroku addons:create heroku-postgresql:mini
git push heroku main

### optional
heroku config:set DISABLE_COLLECTSTATIC=1

#create a superuser
heroku run python manage.py createsuperuser -a radiant-temple-32662

# backup a database
heroku pg:backups:capture --app radiant-temple-32662

### problems with collect static:

disable the collectstatic during a deploy

heroku config:set DISABLE_COLLECTSTATIC=1

deploy

git push heroku master

run migrations (django 1.10 added at least one)

heroku run python manage.py migrate

run collectstatic using bower

heroku run 'bower install --config.interactive=false;grunt prep;python manage.py collectstatic --noinput'

enable collecstatic for future deploys

heroku config:unset DISABLE_COLLECTSTATIC

try it on your own (optional)

heroku run python manage.py collectstatic

future deploys should work as normal from now on