# Cython - interacting with C from Python #

# install #
pip install cython

# load Cython #
%load_ext Cython

# tell the system we will be using Cython keywords #
%%cython

# Cython provides a keyword, cdef which provides access to C types such as char, int, long, float, double, struct and enum. #
cdef int a = 0
for i in range(10):
    a += i
print(a)


# show code generated #
%%cython --annotate

# another example of cdef #
cdef double great_circle(double lon1, double lat1, double lon2, double lat2):
    cdef double a, b, c, radius, theta, x
	
# Since this is no longer standard Python we no longer save it in files with .py extensions, instead by convention we use .pyx. #

# The setup file tells Python how to have Cython build a statically compiled library to call from within Python. #
# This is great_circle_setup_v1.py #
from distutils.core import setup
from Cython.Build import cythonize

setup(
    name='Great Circle v1',
    ext_modules=cythonize("great_circle_v1.pyx"),
)

#  #
$ python great_circle_setup_v1.py build_ext --inplace


