==============
 Installation
==============

Install Ergonomica by running

.. code:: bash

   pip install ergonomica


On first invocation, Ergonomica will create the :code:`~/.ergo` directory, :code:`~/.ergo/.ergo_profile` (initialized as an empty file), as well as the :code:`~/.ergo/packages` directory. Ergonomica will then prompt you with something along the lines of

.. code::

   Do you want to install epm (the Ergonomica Package Manager)? (Y/n):

The Ergonomica Package Manager (EPM) is a tool to download standard Ergonomica packages to add functionality to your shell. It is highly recommended to install it.

FreeBSD Caveat
==============

For some reason, FreeBSD doesn't include the standard python :code:`sqlite3` library by default. You'll have to install it:

.. code::

   pkg install databases/py-sqlite3
   
