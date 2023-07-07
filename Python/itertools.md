#  Itertools provides a set of memory efficient but fast tools, that can be used to provide comprehensive looping features in pure Python. Examples include counting, repetition and grouping. #

# chain #
import itertools
for i in itertools.chain('ABC', 'DEF'):
    print(i)

# count #
from itertools import *
for i in islice(count(), 5, 10):
    print(i)

# permutations: #
from itertools import *
for i in permutations("ABC"):
    print(i)