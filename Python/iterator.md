# iterator definition #
An iterator is an object representing a stream of data; this object returns the data one element at a time. A Python iterator must support a method called __next__() that takes no arguments and always returns the next element of the stream. If there are no more elements in the stream, __next__() must raise the StopIteration exception. Iterators don’t have to be finite, though; it’s perfectly reasonable to write an iterator that produces an infinite stream of data.

# example #
>>> L = [1, 2, 3]
>>>it = iter(L)
>>>it  
<...iterator object at ...>
>>>it.__next__()  # same as next(it)
1
>>>next(it)
2
>>>next(it)
3
>>>next(it)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration

# iterable #
An iterable is an object that has an __iter__ method which returns an iterator, or which defines a __getitem__ method that can take sequential indexes starting from zero (and raises an IndexError when the indexes are no longer valid). So an iterable is an object that you can get an iterator from.

# iterator #
An iterator is an object with a next (Python 2) or __next__ (Python 3) method.

Whenever you use a for loop, or map, or a list comprehension, etc. in Python, the next method is called automatically to get each item from the iterator, thus going through the process of iteration.

# To make an object iterable, you simply have to implement the __getitem__ method #
class T:
    def __getitem__(self, position):
        if position > 5:
         return position
		 
# An iterable must have the following methods: #
an_iterator.__iter__()
an_iterator.__next__()

# A simple version of range() #
class IterateMe_1:
    def __init__(self, stop=5):
        self.current = 0
        self.stop = stop
    def __iter__(self):
        return self
    def __next__(self):
        if self.current < self.stop:
            self.current += 1
            return self.current
        else:
            raise StopIteration

# Now that we know the iterator protocol, we can write something like a for loop: #
def my_for(an_iterable, func):
    """
    Emulation of a for loop.
    func() will be called with each item in an_iterable
    """
    # equiv of "for i in l:"
    iterator = iter(an_iterable)
    while True:
        try:
            i = next(iterator)
        except StopIteration:
            break
        func(i)

# You can create your own iterable by implementing the iteration protocol. #
class fibonacci:
    def __init__(self, max=1000000):
        self.a, self.b = 0, 1
        self.max = max
    def __iter__(self):
        # Return the iterable object (self)
        return self
    def __next__(self):
        # To stop the iteration we just need to raise
        # a StopIteration exception
        if self.a > self.max:
            raise StopIteration
        # save the value that has to be returned
        value_to_be_returned = self.a
        # calculate the next values of the sequence
        self.a, self.b = self.b, self.a + self.b
        return value_to_be_returned

if __name__ == '__main__':
    MY_FIBONACCI_NUMBERS = fibonacci()
    for fibonacci_number in MY_FIBONACCI_NUMBERS:
        print(fibonacci_number)

# and now let’s prove an iterator is stateful… #
"""
Simple iterator examples
"""

class IterateMe_1:
    """

    returns a sequence of numbers
    ( like range() )
    """

    def __init__(self, start, increment, stop):
        self.start = start
        self.increment = increment
        self.stop = stop
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        self.current += self.increment
        if self.current < self.stop:
            return self.current
        else:
            raise StopIteration

if __name__ == "__main__":

    iter = IterateMe_1(5,2,17)
    for i in iter:
        if i >10: break
        print(i)
    # it's stateful
    for i in iter:
        print(i)

    # reinitialize "loses state"
    iter = IterateMe_1(5,2,17)
    for i in iter:
        print(i)
		 