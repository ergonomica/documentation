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
   examples
   configuration
   writing_commands
   releases

   
2.0.0 Released!
===============

This is the first stable release for Ergonomica! To clear a couple of things up:


You Probably Shouldn't Use This As Your Main Shell
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ergonomica is an experimental shell, and as such it doesn't have near the features or support that Fish, Zsh, or Bash have. As such, you'll probably need to use another shell often. However, feel free to use it as long as it's convenient and (please) build extensions for it!

Why 2.0.0? What about 1.0.0?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ergonomica's early, early alpha (3 total rewrites before 2.0.0) was pushed to PyPI as 1.0.0, and the next versions were This version was very unusable and highly unstable. Then, since the rewrite made incompatible API changes, it was changed to 2.0.0-alpha.1, and PyPI versions cant be changed, etc... 2.0.0 is what fits with all Git commit history and thus it is what was chosen.
