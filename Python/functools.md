# The functools module in the standard library provides utilities for working with functions #

# Make a new version of a function with one or more arguments already filled in #
## partial returns a curried function in which one or more parameters of the original function have been given values, so that the returned function will not “ask” for those parameters. ##
from functools import partial

def multiplier(x, n=3):
    return x * n

double_it = partial(multiplier, n=2)
quadruple_it = partial(multiplier, n=4)

>> double_it(4)
8
>> quadruple_it(4)
16