==========
Python API
==========

Ergonomica, being a Python utility, is easy to interface with Python---both as a utility used in Python code as well as a lg

Interfacing with Python


Interfacing in Python
=====================

Assuming you have installed Ergonomica through :code:`pip`, in Python simply import it

.. code:: python
	
	from ergonomica.ergo import ergo

Then, the :code:`ergo()` function in Python will execute any strings passed into it. For example,

.. code:: python

	>>> from ergonomica.ergo import ergo
	>>> ergo('print "hi there folks!"')
	'hi there folks!'


Interfacing with Python
=======================