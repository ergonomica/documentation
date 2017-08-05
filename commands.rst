==========
 Commands
==========

A list of all Ergonomica builtins and standard library functions.

.. note:: In all guides, :code:`.:` represents an Ergonomica prompt---lines without this heading are output of the commands.

Builtins
========

print ARGS...
-------------

Simply returns its output. If passed multiple arguments, will return a list.

Example
~~~~~~~

.. code::

   .: print 1
   1
   .: print 3 2 1
   3
   2
   1

\= ARGS...
----------

Returns :code:`True` if all arguments are equal, :code:`False` otherwise.

Example
~~~~~~~

.. code::

   .: = 2 2 2 2
   True
   .: = 9 10 9 9
   False


!\= ARGS...
-----------

Returns :code:`False` if all arguments are equal, :code:`True` otherwise.

Example
~~~~~~~

.. code::

   != 2 3 4 5
   True
   != 2 2 2 2 2
   False


not BOOL
--------

Returns not of boolean :code:`BOOL` (:code:`False` if :code:`Bool` is :code:`True`, :code:`True` if :code:`Bool` is :code:`False`).

Example
~~~~~~~

.. code::

   .: not #t
   False
   .: not (= 2 3)
   True


sleep SECONDS
-------------

Sleeps for SECONDS seconds, halting the execution of the program.

Example
~~~~~~~

.. code::

   .: sleep 5

\+ ARGS...
----------

Adds all the arguments (this is done with Python :code:`object.__add__`, so lists, strings, etc. may be added).

Example
~~~~~~~

.. code::

   .: + 1 2
   3
   .: + (list 1 2 3) (list 4 5 6)
   1
   2
   3
   4
   5
   6
   .: + testing1 testing2
   testing1testing2

\* ARGS...
----------

Multiplies all the arguments (this is done with Python :code:`object.__mul__`, so is not limited to ints/floats).

Example
~~~~~~~

.. code::

   .: * 3 5
   15
   .: * (list 1 2) 2
   1
   2
   1
   2

   
\- A B
------

Subtracts B from A (i.e., :code:`A-B`).

Example
~~~~~~~

.. code::

   .: - 3 2
   1

   
^ A B
-----

Raises A to the power of B (i.e., :code:`A^B` or :code:`A**B`).

.. note:: :code:`^` is not bitwise XOR like Python's (and other languages') syntax.


Example
~~~~~~~

.. code::

   .: ^ 2 8
   256


/ A B
------

Divides :code:`A` by :code:`B` (i.e., :code:`A/B`.)


Example
~~~~~~~

.. code::

   .: / 2 4
   0.5


<= A B
------

Returns :code:`True` if :code:`A <= B`.


Example
~~~~~~~

.. code::

   .: <= 2 3
   True
   .: <= 4096 4096
   True
   .: <= 4 2
   False


>= A B
------

Returns :code:`True` if :code:`A >= B`.


Example
~~~~~~~

.. code::

   .: >= 4 2
   True
   .: >= 3 3
   True
   .: >= 2 2048
   False


< A B
-----

Returns :code:`True` if :code:`A < B`.


Example
~~~~~~~

.. code::

   .: < 2 3
   True
   .: < 2 3
   False


> A B
-----

Returns :code:`True` if :code:`A > B`.


Example
~~~~~~~

.. code::

   .: > 3 2
   True
   .: > 1 1337
   False


type OBJECT
-----------

Returns the Python type of :code:`OBJECT`.

Example
~~~~~~~

.. code::

   .: type 4
   int
   .: type 4.0
   float
   .: type (list 1 2 3)
   list
   .: type example_string
   str

first ARRAY
-----------

Returns the first element of an array (equivalent to Lisp's :code:`car`).

Example
~~~~~~~

.. code::

   .: first (list 1 2 3 4 5 6)
   1


rest ARRAY
----------

Returns all elements in an array except for the last one (equivalent to Lisp's :code:`cdr`).

Example
~~~~~~~

.. code::

   .: rest (list 1 2 3 4 5 6)
   2
   3
   4
   5
   6


reverse ARRAY
-------------

Returns :code:`ARRAY`, reversed.

Example
~~~~~~~

.. code::

   .: reverse (list 1 5 9)
   9
   5
   1
   .: reverse (reverse (list 1 5 10))
   1
   5
   10


list ARGS...
------------

Returns a list with all the items in :code:`ARGS`.

Example
~~~~~~~

.. code::

   .: list 1 3 2
   1
   3
   2

split STRING SEP
----------------

Splits :code:`STRING` by seperator :code:`SEP`.

Example
~~~~~~~

.. code::

   .: split 1,2,3 ,
   1
   2
   3


flatten LIST
------------

Flattens :code:`LIST`; in other words, if a list of lists (of arbitrary depth0 were a tree, flatten would return its leaves).

Example
~~~~~~~

.. code::

   .: list 1 2 (list 3 (list 4))
   1
   2
   [3, [4]]
   .: flatten (list 1 2 (list 3 (list 4)))
   1
   2
   3
   4


zip ARRAY1 ARRAY2
-----------------

Returns the mixing of these two lists---:code:`[ARRAY1[0], ARRAY2[0], ARRAY1[1], ARRAY2[1]...`. **NOTE**: Does not return a list of tuples as Python's :code:`zip` does.

.. code::

   .: zip (list 1 3 5) (list 2 4 6)
   1
   2
   3
   4
   5
   6

random
------

Returns a random floating-point number between :code:`0.0` and :code:`1.0`.

Example
~~~~~~~

.. code::

   .: random
   0.18886256048003258
   .: random
   0.8792308131952493

randint LOWER [UPPER]
---------------------

Returns a random integer between :code:`LOWER` and :code:`UPPER` (inclusive). If only :code:`LOWER` is specified, the lower bound is set to :code:`0` and the upper limit is set to :code:`LOWER`.

Example
~~~~~~~

.. code::

   .: randint 3
   1
   .: randint 3
   3
   .: randint 10 20
   15


randpick ARRAY
--------------

Returns a random element from :code:`ARRAY`.

Example
~~~~~~~

.. code::

   .: randpick (list 3 9 list)
   list
   .: randpick (list 3 9 list)
   3


round NUM PRECISION
-------------------

Rounds :code:`NUM` to :code:`PRECISION` decimal places.

Example
~~~~~~~

.. code::

   .: round 3.1094 2
   3.11


Constants
=========

Constants are unchangable values in the Ergonomica runtime. These values are prefixed with a :code:`#`. The values are:

- :code:`#t`: the True boolean value
- :code:`#f`: the False boolean value
- :code:`#none`: a NoneType Python object
- :code:`#pi`: The ratio of the diameter to the circumference of a circle (3.1415...)
- :code:`#e`: Euler's Constant (2.7182...)
- :code:`#j`: the imaginary unit (sqrt(-1))

  
Standard Library
================

        
rprompt STRING
--------------

       rprompt: Set the text for the Ergonomica rprompt (next next to prompt).

       Usage:
          rprompt STRING

    
help
----
The Ergonomica help system.

Example
~~~~~~~

.. code::

   .: help commands # lists all commands (including user-defined) in Ergonomica namespace
   ls
   cd
   .
   .
   .

    
mkdir DIR
---------

Make directory :code:`DIR`.

Example
~~~~~~~

.. code::

   .: ls
   example_file.jpeg
   cute_cats.gif
   .: mkdir example_directory
   .: ls
   example_file.jpeg
   cute_cats.gif
   example_directory


cd DIR
------

Changes the directory to :code:`DIR`. If :code:`DIR` not specified, changes to the user's home directory.

Example
~~~~~~~

.. code::

   .: cd
   .: pwd
   /home/ghopper
   .: cd subdir
   .: pwd
   /home/ghopper/subdir
   .: cd
   /home/ghopper


pass
----

Does nothing.

Example
~~~~~~~

.. code::

   .: pass

    
download URL
------------

Download a remote file at URL.

Example
~~~~~~~

.. code::

   .: download http://google.com
   .: read google.com
   <!doctype html><html itemscope=""
   .
   .
   .


cp SOURCE DESTINATION
---------------------

Copies the file at :code:`SOURCE` to :code:`DESTINATION`.

Example
~~~~~~~

find
----
find: Find patterns.

    Usage:
        find PATTERN
        find file PATTERN [-f | --flat] [-s | --strict-path]
        find string PATTERN [-f | --flat]

    Options:
    -f --flat         Do not search recursively (search only the current directory).
    -s --strict-path  Require that file regexp matches full path to the file.

    
quit
----
quit: Exit the Ergonomica shell.

    Usage:
       quit
    
list_modules
------------
list_modules: List all installed modules.

    Usage:
        list_modules
    
title
-----
title: Set the title of the current terminal window to TITLE.

    Usage:
        title TITLE
    
py
--
py: Python ergonomica integration.

    Usage:
       py [(--file FILE | STRING)]
    
ping
----
ping: Ping HOSTNAMEs.

    Usage:
        ping [-c COUNT] HOSTNAMES...

    Options:
        -c --count  Specify the number of times to ping the server.
    
write
-----
write: Write STDIN to file FILE.

    Usage:
        write <file>FILE
    
mv
--
mv: Move files.

    Usage:
       mv TARGET DESTINATION
    
exit
----
exit: Exit the Ergonomica shell.

    Usage:
       exit
    
ls
--

    ls: List files in a directory.

    Usage:
       ls <directory>[DIR] [-c | --count-files][-d | --date] [-h | --hide-dotfiles]

    Options:
       -d --date           Show file creation dates.
       -h --hide-dotfiles  Ignore dotfiles.
       -c --count-files    Return the number of files in a directory.
    
net
---

Various network information commands.

Example
~~~~~~~

.. code::
   
   .: net ip local
   192.168.0.4
   .: net ip global
   38.123.71.82
   .: net mac INTERFACE
   98:e1:d2:a9:c3:e2
   .: net interfaces
   lo
   wlp3s0


size [-u UNIT] FILE...
----------------------

size: Return the sizes of files.

    Usage:
        size [-u UNIT] FILE...

    Options:
        -u, --unit  Specify the unit of size in which to display the file.

    
swap FILE1 FILE2
----------------

Swap the names/contents of two files.

    Usage:
        swap <file>FILE1 <file>FILE2


read FILE
---------

Reads the lines of FILE.

Example
~~~~~~~


    
time
----

    time: Display the current time. FORMAT is in strftime format.

    Usage:
        time [FORMAT]
    
pwd
---

Prints the working directory.


Example
~~~~~~~

.. code::

   .: pwd
   /home/edijkstra

    
rm FILE
-------

Removes file or directory :code:`FILE`.

Example
~~~~~~~

.. code::

   .: ls
   example_dir
   funny_picture.jpeg
   serious_picture.png
   .: rm example_dir
   .: ls
   funny_picture.jpeg
   serious_picture.png
   .: rm funny_picture.jpeg
   .: ls
   serious_picture.png


sysinfo
-------

Provides system-specific information.

Example
~~~~~~~

.. note:: In :code:`sysinfo`, :code:`stat` means static (i.e., unchanging information about the system), whereas :code:`dyn` means dynamic (i.e., values that change).

.. code::

   .: sysinfo stat -a # architecture
   64bit,
   .: sysinfo stat -p # processor
   amdk6
   .: sysinfo stat -r # OS
   Linux-4.12.3-1-ARCH-x86_64-with-arch
   .: sysinfo stat -c # number of cores
   8
   .: sysinfo dyn -u # individual CPU usage percentage
   [1.6, 1.5, 1.8, 1.9]
   .: sysinfo stat -ap # combine and flags and get outputs for each
   64bit,
   amdk6

    
toolbar STRING
--------------

Set the text for the Ergonomica toolbar (bar at bottom of screen).

Example
~~~~~~~

.. code::

   toolbar "MY SUPER COOL TOOLBAR :)"

    
license (show w | show c)
-------------------------

Show Ergonomica license information. If :code:`show c` specified, prints the copyright of Ergonomica. :code:`show w` displays the full text of the GPLv2 license.

Example
~~~~~~~

.. code::

   .: show c
   Ergonomica  Copyright (C) 2017  Liam Schumm, Andy Merrill, Dhyan Patel, Pavel Golubev
   .: show w
                     GNU GENERAL PUBLIC LICENSE
		                          Version 3, 29 June 2007

	Copyright (C) 2007 Free Software Foundation, Inc.
	.
	.
	.


cow STRING
----------

Make a cow say :code:`STRING`.

.. code::

   .: cow 123
    _____
   < 123 >
    -----
       \    ^__^
        \   (oo)\_______
            (__)\        )\/\
                 ||----w |
   	         ||     ||


environment set VARIABLE VALUE
------------------------------

Configure environment variables. :doc:`configuration` has more information on what variables may be set.

Example
~~~~~~~

.. code::   
   .: environment set prompt "[test@home]: "
   [test@home]: # prompt has changed


clear
-----

Clears the screen.


Example
~~~~~~~

.. code::

   .: clear # clears the screen

    
whoami
------

Returns the current user.


Example
~~~~~~~

.. code::

   .: whoami
   kernighan
    
pyvim [FILES...]
----------------

Pure Python Vim clone.

Example
~~~~~~~

.. code::

   pyvim ergo.py # opens ergo.py in pyvim


epm
---

.. note:: :code:`epm` is not integrated with Ergonomica itself, but is bundled for optional installation with the Ergonomica pip installer.

Ergonomica's package manager.

Example
~~~~~~~

.. code::

   .: epm install PACKAGES...     # installs all PACKAGES
   .: epm uninstall PACKAGES...   # uninstalls all PACKAGES
   .: epm packages (local|remote) # lists packages on machine (local) or in repos (remote)
   .: epm repos                   # lists all repos
   .: epm update                  # updates all package listings
   .: epm add-source NAME URL     # add a new repo with a title and URL to a MANIFEST
