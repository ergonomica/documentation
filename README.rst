=============
documentation
=============

Building
========

First, generate documentation for Ergonomica commands by running 

.. code:: bash

	./gen_commands.ergo
	
or in Ergonomica

.. code::
	
	ergo --file gen_commands.ergo
	
Then, to compile the ReStructuredText to :code:`html`, run

.. code::

	make clean && make html