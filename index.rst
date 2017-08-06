.. Ergonomica documentation master file, created by
   sphinx-quickstart on Mon Jul 10 20:28:12 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Ergonomica's Documentation!
======================================

Ergonomica is a cross-platform shell language, implemented in Python. Ergonomica aims to modernize the terminal, in an easily-extensible and usable language, independent of the OS on which it runs. It uses existing core utilities such as the :code:`os` and :code:`shutil` packages, as well as other utilities written in Python, such as the pyvim editor, providing built-in tools that are not os-dependent. Existing Python language features such as asynchronous returning may replace components of the shell such as piping.

To install simply run

.. code::

   pip install ergonomica

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   syntax	     
   commands
   writing_commands
