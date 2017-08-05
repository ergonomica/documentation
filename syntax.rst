Introduction
============

Ergonomica is a fork of Scheme-based, Lisp-like languages. It's not purely functional in that it allows for:

- global/local variable definitions
- commands that have side effects (on the filesystem)

However, ideally all commands will be generally written in a functional manner. It's syntax is that of S-expressions, with a few caveats:

No outer parenthases
~~~~~~~~~~~~~~~~~~~~

.. code:: lisp

   (set x (+ 1 3 2)) # standard Lisp expression

   set x (+ 1 3 2)   # Ergonomica expression

Any strings after the operation in S-Expressions interpreted as strings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this example, the :code:`$` character is used to indicate variable substitution.

.. code:: lisp

   .: set f (lambda (x) x)
   .: f 33
   x
   .: set f (lambda (x) $x)
   .: f 33
   33
   

Functions can have multiple return values (None values filtered out)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: lisp

   .: (set x (lambda (x) (+ x 1) (+ x 2)))
   .: x 33
   34
   35

   
Pipelines
~~~~~~~~~

Ergonomica has piping built into it's S-Expression syntax. These seperate commands and arguments within S-Expressions. All values that are piped are *explicitly specified*, with :code:`{}` syntax. This syntax is built around the concept of *blocks* being passed between items in a pipeline. The simplest example of a pipeline is simply passing all of the output of the previous command, like so

.. code:: lisp

   .: print 1 2 3 | first {}
   1
   .: print 1 2 3 | rest {}
   (2, 3)

However, portions of these blocks may be specified. For example, if we wanted to print every other element, we could create a pipeline with a blocksize of two and always print the 2nd element of that array.

.. code:: lisp

   .: ls
   a.txt
   b.txt
   c.txt
   d.txt
   .: ls | print {1}
   b.txt
   d.txt

The number within the :code:`{}` indicates the index of the item being substituted from standard in.

 Note that in this example, the blocksize was not explicitly specified. Ergonomica reads for the largest index and makes standard in big enough to contain that value. In this example, the block size was 2, resulting in the blocks looking roughly like the following:

 .. code:: lisp

    [[a.txt, b.txt], [c.txt, d.txt]]


Then, filtering for our indices yields the values expected:

.. code:: lisp

   [a.txt, b.txt][1] -> b.txt
   [c.txt, d.txt][1] -> d.txt

However, suppose you want :code:`a.txt` and :code:`c.txt` (i.e., not starting alternating with :code:`b.txt`). Specifying :code:`{0}` would just print every element (a blocksize of one, i.e., a block for every element)

.. code:: lisp

   .: ls | print {0}
   a.txt
   b.txt
   c.txt
   d.txt

You may specify the blocksize explicitly like so:

 .. code:: lisp

    .: ls | print {0/2}
    a.txt
    c.txt

And we have our desired result! :code:`{}` substitution may be done for an arbitrary number of substitutions, in place of regular arguments.
