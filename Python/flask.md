# install #
pip install flask
pip install flask-restful
pip install sqlalchemy

### the simplest example
```python
import os
from flask import Flask

app = Flask(__name__)

@app.route('/hello/')
def hello_world():
    return "Hello, World!"

if __name__ == "__main__":
    port = int(os.environ.get("PORT", 5000))
    app.run(host='0.0.0.0', port=port)
```

# passing an argument #
@app.route('/hello/<name>/')
def hello_world(name):
    return "Hello, {}!".format(name)
	
# using index() function #
@app.route('/')
def index():
	return 'Hello, Flask!'


# simple example using API#
from flask import Flask
from flask_restful import Resource, Api 
from sqlalchemy import createengine 
from flask import jsonify

class Employees(Resource): 
    def get(self):
        conn = db.connect.connect() 
        query = conn.execute("select * from employees")
        result = {"employees": [i[0] for i in query.cursor.fetchall()]}
        conn.close() 
        return jsonify(result)

class Tracks(Resource): 
    def get(self): 
        conn = db.connect.connect() 
        query = conn.execute( "select trackid, name, composer, unitprice from tracks;"
        )
        result = { "data": [dict(zip(tuple(query.keys()), i)) for i in query.cursor]
        }
        conn.close() 
        return jsonify(result)

class Employees_Name(Resource):
    def get(self, employeeid: int): 
        conn = db.connect.connect() 
        query = conn.execute(
        "select * from employees where Employeeid =%d " % int(employee_id)
        )
        result = {"data": [dict(zip(tuple(query.keys()), i)) for i in query.cursor] }
        conn.close() 
        return jsonify(result)
		
if __name__ == "__main__":
    db_connect = create_engine("sqlite:///chinook.db")

    app = Flask(__name__)

    api = Api(app)
    api.add_resource(Employees, "/employees") # Route_1
    api.add_resource(Tracks, "/tracks") # Route_2
    api.add_resource(Employees_Name, "/employees/<employee_id>") # Route_3

    app.run(port="5002")

    db_connect.dispose()
	
# accessing #
127.0.0.1:5002/employees
127.0.0.1:5002/tracks
127.0.0.1:5002/employees/<employee_id> (substituting an employee number where shown)


# string of 16 random bytes #
import os
random_bytes = os.urandom(16)
## b'\xf4\x9f\xb6\xe2Z\x0b@\xa6\x94M\x16\x9b\x85\xb1\xeb\xd9'

# encode random bytes with base64#
import os, base64
code = base64.b32encode(os.urandom(8)).decode().strip("=")

# get secret key from enviroment #
app.secret_key = os.environ.get('SECRET_KEY').encode()

# set enviroment variable for session in Powershell #
$env:SECRET_KEY = "KjJPe35tQKY2YLRzm7vhm3aJdqqh8YHR"

