# On Windows, unlike Linux and Mac, sqlite is not installed with Python. To install on Windows: #
1. Go to https://www.sqlite.org/download.html 
2. Download https://www.sqlite.org/2020/sqlite-tools-win32-x86-3320100.zip
3. Unzip the files in to a directory called c:\sqlite3
4. You may wish to set your path to include c:\sqlite3

# install #
pip install pysqlite3

# to start sqlite3 on Linux and Mac #
sqlite3

# to start sqlite3 on Windows if you didn't set your path to include c:\sqlite3 #
sqlite3 c:\sqlite3\sqlite3

# to return to the command prompt: #
.quit 

# list tables #
.tables

# Start sqlite3 database (from the command line): #
sqlite3 personjob.db

# show the schema #
.schema

# This means that the results of your queries will be displayed in a columnar format #
.mode column

#  sets the width of each column in the output #
.width 15 15 15 15 15

# turns on the display of column headers in the output #
.headers on

# Check version #
sqlite3 -version