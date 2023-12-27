### basic .travis.yml
language: python
python:
  - "3.6"
install:
  - pip install -r requirements.txt
  - python manage.py migrate
script:
  - black --check blogging mysite polling  # Add this line
  - python manage.py test


### registe travis-ci to github
How do I use Travis CI in GitHub?
To get started with Travis CI using GitHub # Go to Travis-ci.com and Sign up with GitHub.