# The preferred import way, rather than using from PeeWee import * #
import peewee as pw

# assign the name of the database file to a variable #
# also creates a database of name file#
file = 'personjob.db'

# need to change that line to be a different connection string. #
db = pw.SqliteDatabase(file)

# the following creates code a little bit cleaner #
# So we don't need to bother to include that in every class. #
# and allows database to be defined changed) in one place #
class BaseModel(pw.Model):

	class Meta:
	database = db

# This class defines Person #
class Person(BaseModel):

	person_name = pw.CharField(primary_key = True, max length = 30)
	lives_in_town = pw CharField(max_length = 40) 
	nickname = pw.CharField(max length = 20, null = True)

	def show(self):
		print(self.person_name, self.lives_in_town, self.nickname)
		
# class with a foreign key #
class Job(BaseModel):
	job name = pwCharField(primary key = True, max length = 30) 
	start_date = pw DateField(formats = 'YYYY-MM-DD')
	end_date = pw DateField(formats = 'YYYY-MM-DD') 
	salary = pw DecimalField(max digits = 7, decimalplaces = 2) 
	person_employed = pw.ForeignKeyField(
		Person, related name='was_filled_by', null = False)
		
#  connect #
db.connect()

# And this is something we specifically need to do in SQLite. #
# It's executing a SQLite SQL statement against the database. #
# And it's an unusual one. #
# SQLite does not enforce foreign key relationships #
# unless we specifically set the foreign key variable PRAGMA #
# to be on in the database. #
db.execute_sql('PRAGMA foreign_keys = ON;')

# creates table #
db.create_tables([ Job, Person ])

# a list uf tuples #
people = [
	('Andrew', 'Sumner', 'Andy'), 
	('Peter', 'Seattle', None), 
	('Susan', 'Boston', 'Beannie'), 
	('Steven', 'Colchester', None), 
	('Peter', 'Seattle', None),
]

# iserting records in a transaction #
for person in people:
	try:
		with db.transaction(): 
			new_person = Person.create( person_name = person[0], livesintown = person[1], nickname = person	[2],) 
			new_person.save() 
	except Exception as e:
		logger.info(f'Error creating person = {person[0}') 
		logger.info(e)
		logger.info('See how the datbase protects our data')
		
# close the connection #
db.close()

# DATASET #
## Create an in-memory SQLite database. ##
db = DataSet('sqlite:///:memory:')

## Get a table reference, creating the table if it does not exist. ##
table = db['users']

## Insert into a table ##
table.insert(name='Huey', age=3, color='white')

## Update ##
table.update(name='Huey', gender='male', columns=['name'])

## Update all records. If the column does not exist, it will be created. ##
table.update(favorite_orm='peewee')

## Using transactions ##
table = db['users']
with db.transaction() as txn:
    table.insert(name='Charlie')

    with db.transaction() as nested_txn:
        # Set Charlie's favorite ORM to Django.
        table.update(name='Charlie', favorite_orm='django', columns=['name'])

        # jk/lol
        nested_txn.rollback()
		
## To retrieve all rows, you can use the all() method ##
### Retrieve all the users. ###
users = db['user'].all()

### We can iterate over all rows without calling `.all()` ###
for user in db['user']:
    print(user['name'])

## Import data from a CSV file into a new table. Columns will be automatically ##
## created for each field in the CSV file. ##
new_table = db['stats']
new_table.thaw(format='csv', filename='monthly_stats.csv')

## A minimal data-loading script might look like this: ##
from playhouse.dataset import DataSet

db = DataSet('sqlite:///:memory:')

table = db['sometable']
table.insert(name='Huey', age=3)
table.insert(name='Mickey', age=5, gender='male')

huey = table.find_one(name='Huey')
print(huey)
# {'age': 3, 'gender': None, 'id': 1, 'name': 'Huey'}

for obj in table:
    print(obj)
# {'age': 3, 'gender': None, 'id': 1, 'name': 'Huey'}
# {'age': 5, 'gender': 'male', 'id': 2, 'name': 'Mickey'}













