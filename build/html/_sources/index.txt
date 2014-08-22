.. _index-file:

Welcome to binario's documentation!
========================================
Package that lets an application read/write primitive data types from an underlying input/output stream as binary data.

Contents
--------
* :ref:`what-is-the-binario`
* :ref:`getting-started`
* :ref:`writer-docs`
* :ref:`reader-docs`

.. toctree::
   :maxdepth: 2

.. _what-is-the-binario:

What is the binario?
--------------------
**binario** is the Python package that lets an application read/write primitive data types from an underlying input/output stream as binary data. It can work with booleans, integers, shorts, long integers, floats, doubles, strings and any byte buffers. 

.. _getting-started:

Getting started
---------------
First of all, install or upgrade package:

>>> pip install binario
>>> pip install binario --upgrade

If you want to write data, create instance of `Writer` and then do your work:

>>> import binario
>>> w = binario.Writer("file.dat")
>>> w.write_short(2014)
>>> w.write_bool(True)
>>> w.write_float(3.1415)
>>> w.write_string("Hello, world!")
>>> w.write(bytes([128, 20, 10, 255, 0]))

Also, if you want to read data, do similar things. Like outputting, create `Reader` and then do your work:

>>> import binario
>>> r = binario.Reader("file.dat")
>>> r.read_short()
2014
>>> r.read_bool()
True
>>> r.read_float()
3.1415
>>> r.read_string()
"Hello, world!"
>>> r.read(5)
b'\x80\x14\n\xff\x00'

By default **binario** use `network` byte order (or `big-endian`). It is can be changed to `little-endian`:

>>> import binario
>>> r = binario.Reader("file.dat", binario.LITTLE_ENDIAN)
>>> w = binario.Writer("another_file.dat", binario.BIG_ENDIAN)

If you want to append new data to existing file, do next:

>>> import binario
>>> w = binario.Writer("incomplete_file.dat", append=True)

