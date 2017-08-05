===============
 Configuration
===============

This guide details how to customize the Ergonomica environments---both cosmetically and functionally.

:code:`.ergo_profile`
=====================

Ergonomica, if loaded with the :code:`--login` flag, will evaluate :code:`~/.ergo/.ergo_profile`. As such, it is typically used as the Ergonomica configuration file. This file is a normal Ergonomica file, and within it you may define variables and commands and execute commands. The :code:`environment` command allows one to set various parameters about your Ergonomica sessions. The following are all the customizable variables of the Ergonomica environments and their defaults:


- :code:`directory`: The current directory in which Ergonomica is in. Defaults to the directory in which Ergonomica is invoked.
- :code:`user`: The current user. Defaults to the user that invokes Ergonomica.
- :code:`home`: The user's home directory. Defaults to what :code:`os` yields for a home directory (:code:`os.getenv(key="HOME")`).
- :code:`welcome`: The message shown after clearing the screen. Defaults to Ergonomica ASCII art:

.. code::
	   ____                              _
	  / __/______ ____  ___  ___  __ _  (_)______ _
	 / _// __/ _ `/ _ \/ _ \/ _ \/  ' \/ / __/ _ `/
	/___/_/  \_, /\___/_//_/\___/_/_/_/_/\__/\_,_/
	        /___/

- :code:`EDITOR`: The user's preferred text editor.
- :code:`LANG`: The user's preferred language. Currently only EN (english) is implemented.
- :code:`prompt`: The user's command-line prompt (known as PS1 in bash). Defaults to :code:`[<directory>]\n.: `; variables that are substituted in (to show relevant information) are :code:`<directory>` (the current directory) and :code:`<user>` (the current user).
- :code:`path`: the PATH used for when looking for commands. Uses `/usr/libexec/path_helper` on Mac---otherwise it might need to be set (depending on what terminal emulator you use).

:code:`toolbar` and :code:`rprompt`
===================================

The :code:`toolbar` and :code:`rprompt` commands allow one to set the content of various display boxes in Ergonomica.
