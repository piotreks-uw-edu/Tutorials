# The Lambda special form is Python's syntax for creating an unnamed function #
lambda arguments: expression

# he function evaluates to the result of the expression.  Here is a lambda that adds one to its argument: #
lambda x: x + 1

# Here is a lambda that adds its two arguments together: #
lambda x, y: x + y

# Compare this syntax to that of a standard function definition: #
def my_sum(x, y):
        return x + y

# This simple function does nothing more than return the value of the expression in the 'return', so it is viable written on a single line. #
def my_sum(x, y): return x + y

# Notice how this named function maps directly to its unnamed, lambda equivalent: #
lambda x, y: x + y

# use the function immediately by calling it with its required arguments #
>>> (lambda x, y: x + y)(2, 3)
5

# or #
>>> adder = lambda x, y:x+y
>>> adder(2, 3)
5
