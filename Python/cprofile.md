# profiler when invoked from the command line #
python -m cProfile great_circle.py

# When invoked from within an interpreter, you can have the profiler be more selective with its reporting. #
>$ ipython

In [1]: %run great_circle.py

In [2]: %prun main()