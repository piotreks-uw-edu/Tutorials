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
heroku config:set DJANGO_ADMIN_USERNAME=piotreks
heroku config:set DJANGO_ADMIN_PASSWORD=Ab12345678
heroku config:set DJANGO_SETTINGS_MODULE=heroku
heroku config:set SECRET_KEY=NnUdYr2888888AuYyppNp33H
heroku addons:create heroku-postgresql:mini
heroku config:set DISABLE_COLLECTSTATIC=1
git push heroku main