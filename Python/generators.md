# definition #
Generators give you an iterator object with no access to the underlying data … if it even exists.  Conceptually, iterators are about various ways to loop over data.  They can generate data on the fly.  In general, you can use either an iterator or a generator — in fact, a generator is a type of iterator.

# Generator functions “yield” a value, rather than returning a value. It *does* ‘return’ a value, but rather than ending execution of the function, it preserves function state #

#  state is preserved between yields #
def a_generator_function(params):
    some_stuff
    yield something
	
# A function with yield in it is a factory for a generator. Each time you call it, you get a new generator: #
gen_a = a_generator()
gen_b = a_generator()

# Each instance keeps its own state. #

# an implementation of range() as a generator: #
def y_range(start, stop, step=1):
    i = start
    while i < stop:
        yield i
        i += step

# Generator Comprehensions: yet another way to make a generator: #	
>>> [x * 2 for x in [1, 2, 3]]
[2, 4, 6]
>>> (x * 2 for x in [1, 2, 3])
<generator object <genexpr> at 0x10911bf50>
>>> for n in (x * 2 for x in [1, 2, 3]):
...   print n
... 2 4 6

# Generators in Python are just another way of creating iterable objects. They are normally used when you need to create an iterable object quickly, without the need of creating a class and adopting the iteration protocol. #
def fibonacci(max):
    a, b = 0, 1
    while a < max:
        yield a
        a, b = b, a+b
if __name__ == '__main__':
    # Create generator of fibonacci numbers
    fibonacci_generator = fibonacci(1000000)
    # print out all the sequence
    for fibonacci_number in fibonacci_generator:
        print(fibonacci_number)
		