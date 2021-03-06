# PyParallel

[![Build Status](https://travis-ci.org/Shapeways/py-parallel.svg?branch=master)](https://travis-ci.org/Shapeways/py-parallel)

Runs a series of functions in parallel processes. Return values are ordered by the order in which their functions
were passed.

```python
val1, val2 = run_parallel([
    lambda: 1 + 1
    lambda: 0])
```

If an exception is raised within one of the processes, that exception will be caught at the process
level and raised by the parent process as an ErrorInProcessException, which will save all errors raised across
processes.

You can catch the exception raised for more details into the process exceptions:

```python
try:
    val1, val2 = run_parallel([fn1, fn2])
except ErrorInProcessException, e:
    print e.errors
```

You can also run using threads or processes:

```python
# Threads
val1, val2 = run_parallel([fn1, fn2])

# Processes
val1, val2 = run_parallel([fn1, fn2], multiprocess=True)
```

# Installation

Using setuptools:

    python setup.py install

Using pip:

    pip install py-parallel
