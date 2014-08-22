.. _writer-docs:

Class `Writer`
==============
Writer lets an application write primitive data types to an underlying output file.

>>> import binario
>>> w = binario.Writer("file.dat")
>>> w.write_short(2014)
>>> w.write_bool(True)
>>> w.write_float(3.1415)
>>> w.write_string("Hello, world!")
>>> w.write(bytes([128, 20, 10, 255, 0]))

.. toctree::
   :maxdepth: 2

__init__(self, file_name, byte_ordering=NETWORK, append=False)
------------------------------------------------------------------
Create new Writer instance and open file for writing. If it necessary, you can specify byte order - `little-endian` or `big-endian`. By default byte order is `network`(`big-endian`). Also you can specify write mode - rewrite existing file or append new data to the end of file. By default it will be rewriting existing files.

>>> import binario
>>> # Open "file_1.dat" with "network" byte order and rewriting mode
>>> w_1 = binario.Writer("file_1.dat")
>>> # Open "file_2.dat" with "network" byte order and append mode
>>> w_2 = binario.Writer("file_2.dat", append=True)
>>> # Open "file_3.dat" with "little-endian" byte order
>>> w_3 = binario.Writer("file_3.dat", binario.LITTLE_ENDIAN)

close(self)
---------------
Closes own output file.

is_closed(self)
-------------------
Check is file already closed.

current_file_size(self)
---------------------------
Return current size of file.

flush(self)
---------------
Flushes this output file.

get_file(self)
------------------
Return current output file. 

write(self, byte)
---------------------
Writes a byte buffer to the underlying output file.
Raise exception when file is already closed.

>>> import binario
>>> w = binario.Writer("file.dat")
>>> w.write(123)
>>> w.write([10, 20, 30])

write_bool(self, flag)
--------------------------
Writes a boolean to the underlying output file as a 1-byte value.

>>> import binario
>>> w = binario.Writer("file.dat")
>>> w.write_bool(True)

write_short(self, number)
-----------------------------
Writes a short integer to the underlying output file as a 2-byte value.

write_int(self, number)
---------------------------
Writes a integer to the underlying output file as a 4-byte value.

write_long(self, number)
----------------------------
Writes a long integer to the underlying output file as a 8-byte value. 

write_string(self, string)
------------------------------
Writes a string to the underlying output file as a buffer of chars with UTF-8 encoding. 

>>> import binario
>>> w = binario.Writer("file.dat")
>>> w.write_string("Hello, World! → ♪")

write_float(self, number)
-----------------------------
Writes a float to the underlying output file as a 4-byte value. 

write_double(self, number)
------------------------------
Writes a double to the underlying output file as a 8-byte value.

>>> import binario
>>> w = binario.Writer("file.dat")
>>> w.write_double(3.14)

:ref:`index-file`
