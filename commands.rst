==========
 Commands
==========

A list of all Ergonomica builtins and standard library functions.

**NOTE**: In all guides, :code:`.:` represents an Ergonomica prompt---lines without this heading are output of the commands.

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

Raises A to the power of B (i.e., :code:`A^B` or :code:`A**B`). *Note*: this is not bitwise XOR like Python's syntax.


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

pyvim
-----

        pyvim: Pure Python Vim clone.

        Usage:
            pyvim [FILES...]
        
rprompt
-------

       rprompt: Set the text for the Ergonomica rprompt (next next to prompt).

       Usage:
          rprompt STRING

    
help
----
help: the Ergonomica help system.
    
    Usage:
        help commands
    
mkdir
-----
mkdir: Make a directory.

    Usage:
       mkdir DIR
    
cd
--
cd: Changes the directory.

    Usage:
        cd [DIR]


pass
----
pass: Does nothing.

    Usage:
       pass
    
download
--------

    download: Download a remote file.

    Usage:
       download URL
    
cp
--
cp: Copy files.

    Usage:
        cp SOURCE DESTINATION
    
removeline
----------
removeline: Remove lines with indices LINENUM from FILE.

    Usage:
        removeline (-f FILE) <int>LINENUM...

    Options:
        -f --file  Specify the file to operate on.
    
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

    
if
--
if: If this, do that.

    Usage:
       if FUNCTION1 FUNCTION2 [FUNCTION3]
    
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
    
graph
-----
graph: Graph numbers in your terminal.
    
    Usage:
        graph NUMBERS...
    
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
    
length
------
length: Return the number of items in STDIN.

    Usage:
        length
        length STRING
    
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
    
print
-----

    print: Print strings.

    Usage:
       print <string>[STRINGS...] [-m MULTIPLIER] [-f INDICES...]

    Options:
       -f --filter     INDICES  Print the items of the input with the specified indices.
       -m --multiplier MULTIPLIER    Print the given item COUNT times (seperated by newlines).
    
mul
---
mul: Multiply a string N times.

    Usage:
        mul STRING N
    
net
---
net: Various network information commands.
    Usage:
        net ip (local|global)
        net mac INTERFACE
        net interfaces
    
size
----
size: Return the sizes of files.

    Usage:
        size [-u UNIT] FILE...

    Options:
        -u, --unit  Specify the unit of size in which to display the file.

    
swap
----
swap: Swap the names/contents of two files.

    Usage:
        swap <file>FILE1 <file>FILE2
    
sort
----
sort: Sort files into folders based on match of regex EXPRESSION in their names.

    Usage:
        sort [DIR=.] EXPRESSION
    
map
---

    map: Map an argument on STDIN.

    Usage:
       map ARGS...
       map -b BLOCKSIZE ARGS...

    Options:
       -i --ignore-blocksize  If the last block is not complete, ignore.
    
users
-----
users: Returns a list of currently logged in users.

    Usage:
        users
    
get
---
get: Get the value of a variable.

    Usage:
       get <variable>VAR
    
read
----

    read: Read a file.

    Usage:
       read FILE
    
time
----

    time: Display the current time. FORMAT is in strftime format.

    Usage:
        time [FORMAT]
    
nequal
------
nequal: Compare if arguments are not equal.

    Usage:
       nequal A B
    
pwd
---
pwd: Print the working directory.

    Usage:
        pwd
    
rm
--
rm: Remove files and directories.

    Usage:
       rm <file/directory>FILE
    
write_documentation_with_command
--------------------------------
usage: function COMMAND
addstring
---------
addstring: Add all strings from STDIN.

    Usage:
       addstring [-s | --separator SEPARATOR]
    
    
sysinfo
-------

    sysinfo: Print system information

    Usage:
       sysinfo stat [-apr]
       sysinfo dyn  [-cu]

    Options:
       -a --architecture   Print the system bits as well as linkage.
       -p --processor      Print processor name.
       -o --os             Print OS common name.
       -c --cpu-count       Print the number of CPUs on the system.
       -u --percent-usage  Print percent CPU usage for each CPU.
    
toolbar
-------

       toolbar: Set the text for the Ergonomica toolbar (bar at bottom of screen).

       Usage:
          toolbar STRING
    
license
-------
license: Return Ergonomica license information.

    Usage:
        license (show w|show c)
    
cow
---
cow: Make a cow say STRING.

    Usage:
        cow STRING
    
environment
-----------

       environment: Configure environment variables.

       Usage:
          environment set VARIABLE VALUE
          environment macro add REGEXP REPLACEMENT
          environment alias add COMMAND REPLACEMENT
    
split
-----
split: Split a string.

    Usage:
        split STRING SEP
    
clear
-----
clear: Clear the screen.

    Usage:
       clear
    
equal
-----
equal: Compare equality of arguments.

    Usage:
        equal A B
    
try
---
try: handle error catching
    
    Usage:
        try BODY
        try BODY EXCEPTION
    
alias
-----
alias: Map commands to names.
    Usage:
        alias NAME FUNCTION
    
while
-----
while: While CONDITION returns true, do BODY.

    Usage:
        while CONDITION BODY
    
epm
---
epm: Ergonomica's package manager.

    Usage:
        epm install PACKAGES...
        epm uninstall PACKAGES...
        epm packages (local|remote)
        epm repos
        epm update
        epm add-source NAME URL
    
whoami
------
whoami: Return the current user.

    Usage:
       whoami
    
