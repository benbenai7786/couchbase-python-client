pylibcouchbase
==============

This is an experimental repository for the next generation Couchbase Python
SDK which is based on [libcouchbase][1].

The couchbase.pxd was automatically generated by a [cwrap branch that uses
libclang][2].


Prerequisites
-------------

Install libcouchbase.


Building
--------

If you have a source checkout via Git you need to have Cython (>=0.19)
installed in order to generate the `couchbase/libcouchbase.c` file. If you've
downloaded the source package the file is already included.

As the target audience is currently developers, you probably want to install
the module locally. You can run:

    python setup.py build_ext --inplace

If you have compile libcouchbase yourself at a custom location, you can pass
it in via the `CFLAGS` and `LDFLAGS` environment variables.


Running sample application
--------------------------

To run the small sample application that inserts one million documents into
a local Couchbase at the default port 8091 and a bucket called "default",
just execute:

    python examples/basic.py


Building documentaion
---------------------

The documentation is using Sphinx and also needs the numpydoc Sphinx extension.
To build the documentation, go into the `docs` directory and run:

    make html

The HTML output can be found in `docs/build/html/`.


Running tests
-------------

The tests need a running Couchbase instance. The values to connect to the
instance can be found in the test configuration file `tests/tests.ini`.

The test suite need several buckets which need to be created before the tests
are run. They will all have the common prefix as specified in the test
configuration file. To create them, run:

    python tests/setup_tests.py

If the buckets already exist, they will be recreated.

Now you can run the test. If you have Python >=2.7 or >=3.2 you can run:

    python -m unittest discover -s tests

Or if you have `nose` installed, you can also run:

    nosetests


Tested platforms
----------------

So far the code has been tested on the following platforms/environments.

Linux 64-bit (with GCC):

 - Python 2.7.3
 - Python 3.2.3
 - PyPy 1.9

OSX (with clang):

 - Python 2.7


If you ran it on a different platform and it worked, please let me know and
I'll add it to the list.


License
-------

pylibcouchbase is licensed under the Apache License 2.0.



[1]: https://github.com/couchbase/libcouchbase
[2]: https://github.com/geggo/cwrap
