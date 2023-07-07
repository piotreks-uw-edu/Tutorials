# PySnooper allows you to selectively see, or 'snoop', upon what your Python program is doing. 
# It helps you answer questions like "which statements are executing", 
# or "which if statements are passing and failing", or even "how did that variable get that value".

# installing
python -m pip install pysnooper

# watches what is going on
import pysnooper

class Memoize:
	def init_ (self, fn): self.fn = fn self.memo = {} def call_ (self, *args): if args not in self.memo:
		print(f"memoizing {args}")
		self.memo[args = self.fn(*args)
	else:
		print(f"not memoizing {args} - done already")
		return self.memo[args]

@Memoize
def fib(n):
	...
	
# setting the depth to snoop, here we.r a snooping on a main() function, but we can snoop on any function
@pysnooper.snoop(depth=3)
def main()

# Say you have a function called calculate_roi() that performs a very complex calculation.
# And it isn't working right. All you do is:
python -m pip install pysnooper

# Then you must:
import pysnooper

# And then, immediately before def calculate_roi() you add @pysnooper.snoop(). So the code looks like this:
@pysnooper.snoop()
def calculate_roi()
    # blah blah blah

