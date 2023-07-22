# Currying is a technique where you reduce the number of parameters a function takes #
## insted fo 2 arguments in: ##
def multiplier(x, n=3):
    return x * n
	
## we get 1 argument ##
def get_multiplier(n = 3):
    def multiplier(x)
        return x * n
    return multiplier
	
# Another example #
# introductions.py
def introduce_person(name, age, job, location):
    return "This is %s, a %d-year-old %s living in %s" % (name, age, job, location)
	
>>> from introductions import introduce_person
>>> introduce_person("Elisa", 28, "engineer", "Portland")
'This is Elisa, a 28-year-old engineer living in Portland'

# This works well, but it might seem less convenient if you have a list of people you need to introduce, all with the same job (for example, ‘student’), all with the same age (maybe 4th grade children) who all happen to be 10 years old and all living in the same city. Only the names are changing. #
def get_simple_intro(age, job, location):
    def simple_introduction(name):
        return "This is %s, a %d-year-old %s living in %s" % (name, age, job, location)
    return simple_intro
>> simple_intro = get_simple_intro(10, 'student', 'Seattle')
>> simple_intro('Maya')
'This is Maya, a 10-year-old student living in Seattle'
>> simple_intro('Alison')
'This is Alison, a 10-year-old student living in Seattle'

# currying with functools.partial (based on above example)#
>>> from introductions import introduce_person
>>> from functools import partial
>>> simple_intro = partial(introduce_person, age=10, job='student', location='Seattle')
>>> simple_intro('Letty')
'This is Letty, a 10-year-old student living in Seattle'