# Import the `timeit` function from the `timeit` module and rename it as `timer`.
# However, in this code, the timer is not actually used.

from timeit import timeit as timer

# Define the number of repetitions for a timeit function.
# However, in this code, the repetitions is not actually used.
repetitions = 10000

# Define the range of numbers for our list.
my_range = 10000

# Define the lower limit as half of my_range.
lower_limit = my_range / 2

# Create a list of integers from 0 up to but not including my_range.
my_list = list(range(my_range))


# Define a function that multiplies the input by two.
def multiply_by_two(x):
    return x * 2


# Define a function that checks if the input is greater than the lower_limit.
def greater_than_lower_limit(x):
    return x > lower_limit


print("\n\nmap_filter_with_functions")
print(timer(
    'map_filter_with_functions = map(multiply_by_two, filter(greater_than_lower_limit, my_list))',
    globals=globals(),
    number=repetitions
))

# print(*map_filter_with_functions)

print("\n\nmap_filter_with_lambdas")
print(timer(
    'map_filter_with_lambdas = map(lambda x: x * 2, filter(lambda x: x > lower_limit, my_list))',
    globals=globals(),
    number=repetitions
))
# print(*map_filter_with_lambdas)

print("\n\ncomprehension")
print(timer(
    'comprehension = [x * 2 for x in my_list if x > lower_limit]',
    globals=globals(),
    number=repetitions
))
# print(*comprehension)

print("\n\ncomprehension_with_functions")
print(timer(
    'comprehension_with_functions = [multiply_by_two(x) for x in my_list if greater_than_lower_limit(x)]',
    globals=globals(),
    number=repetitions
))
# print(*comprehension_with_functions)

print("\n\ncomprehension_with_lambdas")
print(timer(
    'comprehension_with_lambdas = [(lambda x: x * 2)(x) for x in my_list if (lambda x: x > lower_limit)(x)]',
    globals=globals(),
    number=repetitions
))
# print(*comprehension_with_lambdas)