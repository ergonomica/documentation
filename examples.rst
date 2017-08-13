==========
 Examples
==========

This page lists a variety of (hopefully) common applications of the shell, and how to perform these in Ergonomica.

Replace instances of a word in a file
=====================================

.. code::

   .: read a.txt
   this is Example
   Test which is an Example
   of a file
   .: read a.txt | replace Example test {0} | write a.txt {}
   
Explanation
-----------
   
Firstly, :code:`read a.txt` reads the list of lines of the file :code:`a.txt` and reads it into an array of lines. The :code:`replace` command is then used, for each line, to replace instances of Example with test. The :code:`{0}` character indicates that every 0-th item in the array of lines should be operated on (out of 1 items), applying this to each file. Then, the list of all processed lines, or :code:`{}`, are written back to :code:`a.txt`.


Remove all .pyc files recursively
=================================

.. code::

   .: find file .*pyc | rm {0}

Explanation
-----------

The command `find file .*pyc` finds all files in the current directory or any subdirectory (of arbitary depth) that matches the regex :code:`.*pyc` (aka all strings ending with :code:`pyc`). `rm` then removes each `0`-th file in this list of files, in other word every file.


Add hashbangs to any Python file (if they don't exist)
======================================================

.. code::

   .: find file .*py | if (not (?contains (read {0}) "#!/usr/bin/env python"))
                          (write {0} (+ (list "#!/usr/bin/env python") (read {0})))

			  
