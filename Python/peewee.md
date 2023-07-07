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
