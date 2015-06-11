# PyParallel

[![Build Status](https://travis-ci.org/Shapeways/py-parallel.svg?branch=master)](https://travis-ci.org/Shapeways/py-parallel)

Runs a series of functions in parallel processes. Return values are ordered by the order in which their functions
were passed.

    val1, val2 = run_parallel(
        lambda: 1 + 1
        lambda: 0
    )

If an exception is raised within one of the processes, that exception will be caught at the process
level and raised by the parent process as an ErrorInProcessException, which will track all errors raised in all
processes.

You can catch the exception raised for more details into the process exceptions:

    try:
        val1, val2 = run_parallel(fn1, fn2)
    except ErrorInProcessException, e:
        print.e.errors

