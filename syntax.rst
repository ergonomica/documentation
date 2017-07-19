========
 Syntax
========

Ergonomica's syntax aims to be both ergonomic, conveninent, and easy to understand. Thus, it accepts POSIX standards for command arguments, e.g.,

.. code::

	command arg1 arg2 --option --option-with-argument ARG -o
	
It also supports piping, using the pipe character (:code:`|`), like so


.. code::

	ls | map rm {}
	
where :code:`ls` lists all the files in the current directory, and :code:`map` applies the :code:`rm` command to each command listed.

Backgrounding Processes
=======================

A process may be started in the background by prefixing your command with :code:`(bg)`, like so

.. code::

	(bg)some_long_running_command
	
This :code:`(bg)` command does not care about any special syntax; it just makes the entire line of input backgrounded/ This should be changed.

 However, aside from these, there are no special characters in Ergonomica.