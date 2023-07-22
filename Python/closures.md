# closure is a function that "remembers" the environment where it was created. For instance, consider a nested function #
def outer_function():
    variable = "I am a variable from the outer function"

    def inner_function():
        print(variable)

    return inner_function

new_function = outer_function()
new_function()  # prints: "I am a variable from the outer function"


# Closures act as factories for new functions, simplifying a process that would otherwise need additional code #
def multiply(x):
    return x * 3
	
def make_multipler(n):
    def multiply(x):
        return x * n
    return multiply	
	
times3 = make_multiplier(3)
times3(4)
>> 12
times5 = make_multiplier(5)
times5(4) 
>>20

# nonlocal *keyword allows to use the *counter variable from the enclosing function without making it a global variable #
1 def counter(start=0):
2     count = start
3     def increment():
4         nonlocal count
5         count += 1
6         return count
7     return increment

mycounter = counter(0) # Creates one counter
mysecondcounter = counter(0) # Creates a second, INDEPENDENT counter

mycounter()
>> 1
mycounter()
>> 2
mysecondcounter()
>> 1