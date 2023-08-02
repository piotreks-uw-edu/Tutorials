# A decorator is a function that takes a function as an argument and returns a function as a return value. #

## example ##
def goodbye():
    print('goodbye')

def mydecorator(func):
    def hello():
        print('hello')
    return hello

# REFERENCE POINT
goodbye = mydecorator(goodbye)
goodbye()
>> hello

# now the same using decorator syntax
# does the same as REFERENCE POINT
@mydecorator
def yada():
    print('yada')

yada()
>> hello
## end of example ##