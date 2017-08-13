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

apply FUNCTION ARGS
-------------------

Runs :code:`FUNCTION` with arguments :code:`ARGS`.

Example
~~~~~~~

.. code::

   .: set x (list 1 2 3)
   .: apply $= $x
   False
   
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

accum OPERATOR LIST
-------------------

Notating :code:`OPERATOR` by :code:`#`, :code:`accum` returns

.. code::

   ((LIST[0] # LIST[1]) # LIST[2]) # LIST[3])...

Example
~~~~~~~

.. code::

   .: accum $- (list 1 2 3 4)
   -8

.. note:: Just using :code:`-` here wouldn't be sufficient since any token after the function (:code:`accum` here) will be interpreted as a string unless it has a :code:`$` prefix.
   

search REGEX
------

Searches (and returns) all matches of :code:`REGEX` in :code:`STRING`.

Example
~~~~~~~

.. code::

   .: search "[A-Z][a-z]+" "This is a String."
   This
   String


replace REGEX SUB STRING
------------------------

Replaces all matches of :code:`REGEX` in :code:`STRING` with :code:`SUB`.

Example
~~~~~~~

.. code::

   .: replace "[a-z]" "9" basfdbasdifbas4145
   999999999999994145
   .: replace silly serious "this is a very silly string"
   this is a very serious string


?file FILE
----------

Returns :code:`True` if :code:`FILE` is a valid file, :code:`False` if it isn't.

Example
~~~~~~~

.. code::

   .: ?file /etc/fstab
   True
   .: ?file /etc
   False
   .: ?file /qj0jq0-9qri0w5i0q9wi0tiw09ti
   False


?dir DIR
--------

Returns :code:`True` if :code:`DIR` is a valid directory, :code:`False` if it isn't.

Example
~~~~~~~

.. code::

   .: ?dir /etc
   True
   .: ?dir /etc/fstab
   False

?contains ITEM LIST
-------------------

Returns :code:`True` if :code:`ITEM` is within :code:`LIST`, :code:`False` if it isn't.

Example
~~~~~~~

.. code::

   .: ?contains 123123 (list 123123 44 444)
   True
   .: ?contains "not contained" (list "it really isn't" "contained")
   False


?match REGEX STRING
-------------------

Returns the match of :code:`REGEX` in :code:`STRING` (if it matches), else it returns :code:`False`.

.. code::

   .: match "[a-c]+" "abababababc"
   abababababc
   .: match "[a-c]+" "ddddd"
   False

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

Set the text for the Ergonomica rprompt (next next to prompt).

Example
~~~~~~~

.. code::

   rprompt "hi there :p"

    
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

temp
----

Returns a valid temporary file or directory valid for the current operating system.

Example
~~~~~~~

.. code::
   .: temp file
   /tmp/tmp5hismn70
   .: temp dir
   /tmp/tmp42d49ak9


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

.. code::

   .: ls
   a.txt
   .: read a.txt
   here is my file!
   :) catch you on the flipside!
   .: cp a.txt b.txt
   .: ls
   a.txt
   b.txt
   .: read b.txt
   here is my file!
   catch you on the flipside!

find
----

Find files and patterns within files.

Example
~~~~~~~

.. code::

   .: find file .*rst # match files with regex
   ./a/b.rst
   ./c.rst
   ./z/example.rst
   .: find -f file .*rst # -f or --flat means search only in current dir
   ./c.rst
   .: find -s file [^z]*rst # -s mandates the regexp must match the full path
   ./a/b.rst
   ./c.rst
   .: find -sf file [^z]*rst # combine flags
   ./c.rst
   .: find string 2.71828 # find strings in files
   ./c.rst: return 2.71828 + 3
   ./z/example.rst: return "My favorite number is 2.71828!!!"
   .: find -f string 2.71828 # also limit your search to the current dir
   ./c.rst: return 2.71828 + 3


quit
----

Exits the Ergonomica shell.

Example
~~~~~~~

.. code::

   quit


list_modules
------------
List all installed modules (packages in :code:`~/.ergo/packages`).

Example
~~~~~~~

.. code::

   .: list_modules
   epm
   vortex


title TITLE
-----------

Set the title of the current terminal window to TITLE.

Example
~~~~~~~

.. code::

   .: title "My Super COOl Terminal!11"

    
py
---

Python ergonomica integration.


Example
~~~~~~~

.. code::

   .: py "1+1" # simple expressions
   2
   .: py "l = 2" # set variables...
   .: print $l   # and get them in the Ergonomica namespace!
   2
   .: py # open up the PtPython REPL (all variables here are also shared)
   >>>
   .
   .
   .


ping
----

ping: Ping HOSTNAMEs.

Example
~~~~~~~

.. warning:: The output won't be exactly what's shown here; there'll likely be some output printed to STDOUT (since this calls a system process); however what is shown here is what is actually returned by this function.

.. code::

   .: ping 8.8.8.8 
   8.8.8.8 is up # returned on ctrl-c (ping process continues to run)
   .: ping -c 2 8.8.8.8 INVALIDADDRESS
   8.8.8.8 is up
   INVALIDADDRESS is down


write [-a] FILE [LINES...]
--------------------------

Write lines to a file. Will overwrite file unless :code:`-a` (append) option is called.

Example
~~~~~~~

.. code::

   .: ls
   unrelated.jpeg
   .: write test_file 123123 # create a new file
   .: ls
   test_file
   unrelated.jpeg
   .: read test_file
   123123
   .: write test_file -a abcabc # only appends; does not overwrite
   .: read test_file
   123123
   abcabc

    
mv TARGET DESTINATION
---------------------

Move a file from :code:`TARGET` to :code:`DESTINATION`.

Example
~~~~~~~

.. code::

   .: ls
   a.txt
   .: mv a.txt b.txt
   .: ls
   b.txt


exit
----

Exits the Ergonomica shell.

Example
~~~~~~~

.. code::

   exit



ls <directory>[DIR] [-c | --count-files][-d | --date] [-h | --hide-dotfiles]
----------------------------------------------------------------------------

List files in a directory.

Example
~~~~~~~

.. warning:: :code:`ls` shows dotfiles by default. To disable this, use the :code:`-h` or :code:`--hide-dotfiles` flag.

.. code::

   .: ls # list files as you normally would
   .example_dotfile
   a.txt
   b.c
   a.out
   .: ls -d # list the creation dates
   2012-18-03 09:35:21.293598 .example_dotfile
   2015-21-04 08:29:46.981327 a.txt
   2017-02-09 02:96:93.191238 b.c
   2016-13-02 04:38:72.912840 a.out
   .: ls -h # hide dotfiles
   a.txt
   b.c
   a.out
   .: ls -c # return the number of files in a directory
   4
   .: ls -ch # count files without dotfiles
    
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


environment
-----------

Configure environment variables. :doc:`configuration` has more information on what variables may be set.

Example
~~~~~~~

.. code::   
   .: environment set prompt "[test@home]: "
   [test@home]: # prompt has changed
   .: environment get prompt
   [test@home]:


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
