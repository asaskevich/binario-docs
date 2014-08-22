.. _reader-docs:

Class `Reader`
==============
Reader lets an application read primitive data types from an underlying input file.

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

.. toctree::
   :maxdepth: 2

__init__(self, file_name, byte_ordering=NETWORK)
------------------------------------------------
Create new Reader instance and open file for reading. If it necessary, you can specify byte order - `little-endian` or `big-endian`. By default byte order is `network`(`big-endian`).

>>> import binario
>>> r_1 = binario.Reader("file_1.dat")
>>> r_2 = binario.Reader("file_2.dat", binario.LITTLE_ENDIAN)

close(self)
-----------
Closes this input file. 

is_closed(self)
---------------
Check is input file already closed. 

flush(self)
-----------
Flushes this input file. 

get_file(self)
--------------
Return current input file. 

get_position(self)
------------------
Return count of bytes already taken from the input file. 

get_file_size(self)
-------------------
Returns the length of the file. 

is_eof(self)
------------
Check is already reached end of file. 

get_remaining_size(self)
------------------------
Return remaining count of bytes, available for reading. 

seek(self, pos)
---------------
Move to new input file position. If position is negative or out of file, raise Exception. 

read(self, size=1)
------------------
Read byte buffer with specified size from input file.

Raise exception in two cases:
- File already closed.
- Not enough data to read.

Keyword arguments:
size -- size of buffer to read (default 1)

>>> import binario
>>> r = binario.Reader("file.dat")
>>> r.read(5)
b'\x80\x14\n\xff\x00'

read_string(self)
-----------------
Read string from input file with UTF-8 encoding. 

read_byte(self)
---------------
Read byte from input file. 

read_bool(self)
---------------
Read boolean from the underlying input file as a 1-byte value. 

read_int(self)
--------------
Read signed integer from the underlying input file as a 4-byte value.  

read_short(self)
----------------
Read signed short from the underlying input file as a 2-byte value.  

read_long(self)
---------------
Read signed long from the underlying input file as a 8-byte value.  

read_float(self)
----------------
Read float from the underlying input file as a 4-byte value.  

read_double(self)
-----------------
Read double from the underlying input file as a 8-byte value.  

:ref:`index-file`