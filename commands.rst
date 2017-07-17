load
----

    load: Load a file into ergonomica.

    Usage:
       load FILE
    
pyvim
-----

        pyvim: Pure Python Vim clone.

        Usage:
            pyvim [FILES...]
        
rprompt
-------

       rprompt: Set the text for the Ergonomica rprompt (next next to prompt).

       Usage:
          rprompt STRING

    
shuffle
-------
shuffle: Shuffle STDIN.

    Usage:
        shuffle
    
help
----
help: the Ergonomica help system.
    
    Usage:
        help command COMMAND
        help commands
    
true
----
true: Return true.

    Usage:
       true
    
mkdir
-----
mkdir: Make a directory.

    Usage:
       mkdir DIR
    
cd
--
cd: Changes the directory.

    Usage:
        cd [DIR]
    
set
---
set: Set variables.

    Usage:
       set <variable>VAR VAL
    
pass
----
pass: Does nothing.

    Usage:
       pass
    
download
--------

    download: Download a remote file.

    Usage:
       download URL
    
false
-----
false: Return false.

    Usage:
       f
    
cp
--
cp: Copy files.

    Usage:
        cp SOURCE DESTINATION
    
removeline
----------
removeline: Remove lines with indices LINENUM from FILE.

    Usage:
        removeline (-f FILE) <int>LINENUM...

    Options:
        -f --file  Specify the file to operate on.
    
find
----
find: Find patterns.

    Usage:
        find PATTERN
        find file PATTERN [-f | --flat] [-s | --strict-path]
        find string PATTERN [-f | --flat]

    Options:
    -f --flat         Do not search recursively (search only the current directory).
    -s --strict-path  Require that file regexp matches full path to the file.

    
if
--
if: If this, do that.

    Usage:
       if FUNCTION1 FUNCTION2 [FUNCTION3]
    
quit
----
quit: Exit the Ergonomica shell.

    Usage:
       quit
    
list_modules
------------
list_modules: List all installed modules.

    Usage:
        list_modules
    
title
-----
title: Set the title of the current terminal window to TITLE.

    Usage:
        title TITLE
    
graph
-----
graph: Graph numbers in your terminal.
    
    Usage:
        graph NUMBERS...
    
py
--
py: Python ergonomica integration.

    Usage:
       py [(--file FILE | STRING)]
    
ping
----
ping: Ping HOSTNAMEs.

    Usage:
        ping [-c COUNT] HOSTNAMES...

    Options:
        -c --count  Specify the number of times to ping the server.
    
length
------
length: Return the number of items in STDIN.

    Usage:
        length
        length STRING
    
write
-----
write: Write STDIN to file FILE.

    Usage:
        write <file>FILE
    
mv
--
mv: Move files.

    Usage:
       mv TARGET DESTINATION
    
exit
----
exit: Exit the Ergonomica shell.

    Usage:
       exit
    
ls
--

    ls: List files in a directory.

    Usage:
       ls <directory>[DIR] [-c | --count-files][-d | --date] [-h | --hide-dotfiles]

    Options:
       -d --date           Show file creation dates.
       -h --hide-dotfiles  Ignore dotfiles.
       -c --count-files    Return the number of files in a directory.
    
print
-----

    print: Print strings.

    Usage:
       print <string>[STRINGS...] [-m MULTIPLIER] [-f INDICES...]

    Options:
       -f --filter     INDICES  Print the items of the input with the specified indices.
       -m --multiplier MULTIPLIER    Print the given item COUNT times (seperated by newlines).
    
mul
---
mul: Multiply a string N times.

    Usage:
        mul STRING N
    
net
---
net: Various network information commands.
    Usage:
        net ip (local|global)
        net mac INTERFACE
        net interfaces
    
size
----
size: Return the sizes of files.

    Usage:
        size [-u UNIT] FILE...

    Options:
        -u, --unit  Specify the unit of size in which to display the file.

    
swap
----
swap: Swap the names/contents of two files.

    Usage:
        swap <file>FILE1 <file>FILE2
    
sort
----
sort: Sort files into folders based on match of regex EXPRESSION in their names.

    Usage:
        sort [DIR=.] EXPRESSION
    
map
---

    map: Map an argument on STDIN.

    Usage:
       map ARGS...
       map -b BLOCKSIZE ARGS...

    Options:
       -i --ignore-blocksize  If the last block is not complete, ignore.
    
users
-----
users: Returns a list of currently logged in users.

    Usage:
        users
    
get
---
get: Get the value of a variable.

    Usage:
       get <variable>VAR
    
read
----

    read: Read a file.

    Usage:
       read FILE
    
time
----

    time: Display the current time. FORMAT is in strftime format.

    Usage:
        time [FORMAT]
    
nequal
------
nequal: Compare if arguments are not equal.

    Usage:
       nequal A B
    
pwd
---
pwd: Print the working directory.

    Usage:
        pwd
    
rm
--
rm: Remove files and directories.

    Usage:
       rm <file/directory>FILE
    
write_documentation_with_command
--------------------------------
usage: function COMMAND
addstring
---------
addstring: Add all strings from STDIN.

    Usage:
       addstring [-s | --separator SEPARATOR]
    
    
sysinfo
-------

    sysinfo: Print system information

    Usage:
       sysinfo stat [-apr]
       sysinfo dyn  [-cu]

    Options:
       -a --architecture   Print the system bits as well as linkage.
       -p --processor      Print processor name.
       -o --os             Print OS common name.
       -c --cpu-count       Print the number of CPUs on the system.
       -u --percent-usage  Print percent CPU usage for each CPU.
    
toolbar
-------

       toolbar: Set the text for the Ergonomica toolbar (bar at bottom of screen).

       Usage:
          toolbar STRING
    
license
-------
license: Return Ergonomica license information.

    Usage:
        license (show w|show c)
    
cow
---
cow: Make a cow say STRING.

    Usage:
        cow STRING
    
environment
-----------

       environment: Configure environment variables.

       Usage:
          environment set VARIABLE VALUE
          environment macro add REGEXP REPLACEMENT
          environment alias add COMMAND REPLACEMENT
    
split
-----
split: Split a string.

    Usage:
        split STRING SEP
    
clear
-----
clear: Clear the screen.

    Usage:
       clear
    
equal
-----
equal: Compare equality of arguments.

    Usage:
        equal A B
    
try
---
try: handle error catching
    
    Usage:
        try BODY
        try BODY EXCEPTION
    
alias
-----
alias: Map commands to names.
    Usage:
        alias NAME FUNCTION
    
while
-----
while: While CONDITION returns true, do BODY.

    Usage:
        while CONDITION BODY
    
epm
---
epm: Ergonomica's package manager.

    Usage:
        epm install PACKAGES...
        epm uninstall PACKAGES...
        epm packages (local|remote)
        epm repos
        epm update
        epm add-source NAME URL
    
macro
-----
macro: Defines a text macro mapping STRING to REPLACEMENT_STRING.

    Usage:
        macro STRING REPLACEMENT_STRING
    
whoami
------
whoami: Return the current user.

    Usage:
       whoami
    