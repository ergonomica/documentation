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

			  
Define a function to go up one directory N times
================================================

.. code::

   set up (lambda (n) (
           if (!= n 0) (
	       up (- $n 1)))
	   (cd ..))


Explanation
~~~~~~~~~~~

This defines a function, :code:`up`, which operates recursively on a depth :code:`n`. Until :code:`n` is 0, it invokes itself again (decrementing :code:`n` by 1), going up one directory level each time, until :code:`n` reaches :code:`0`.

Find all directories 7 directory levels down that have more than two items
==========================================================================


.. code::
   .: set is7dirsdown (lambda (dir) (= (count "/" dir) 7))
   .: set containsmorethan2items (lambda (dir) (> (len (ls $dir)) 1))
   .: filter $containsmorethan2items (filter $is7dirsdown (find dir .*))

Explanation
~~~~~~~~~~~

This program hinges on the fact that we can separate our conditional into two different statements---"is 7 directories down" and "contains more than 2 items". We create two functions that return boolean values as to whether their inputs fulfill these conditions. Then, we first filter by our "7 directories down" condition, and then our "contains more than 2 items" condition.

.. note:: Here, we must prefix each function that we're filtering with with a :code:`$`, because otherwise they would be interpreted as strings. Functions are values in the namespace just as any other variable.