
###########
NCM\::Check
###########


****
NAME
****


NCM::Check - control the state of system files


***********
INHERITANCE
***********


Derives from ``LC::Check``.  Most functions are described in the ``LC::Check``
manpage.


********
SYNOPSIS
********



.. code-block:: perl

   use NCM::Check;
 
   NCM::Check::lines('/filename',
     backup => ".suffix",
     linere => "regexp",
     goodre => "regexp",
     good   => "string",
     keep   => ("first" || "last" || "all"),
     add    => ("first" || "last" || "no"));



***********
DESCRIPTION
***********


``NCM::Check`` is a suite of functions to control the state of configuration files.
If the files are not correct, ``NCM::Check`` will amend them.  Various
properties may be controlled, including:


- \*
 
 Existence of file (creation or deletion as necessary)
 


- \*
 
 Presence of lines in a text file (added, rewritten or deleted as necessary)
 


- \*
 
 File mode, owner, access time, hard and soft links, ...
 



*******
METHODS
*******


NCM::Check::lines(file [, option ...])
======================================


Ensures that specified lines are present in \ *file*\ .

A newline will be appended to the file if the last line is not newline-terminated.

Options:


- linere
 
 Only lines matching /\ *linere*\ / will be considered.
 


- goodre
 
 Lines matching /\ *goodre*\ / will be preserved unchanged.
 


- good
 
 String to replace lines that match /\ *linere*\ / but not /\ *goodre*\ /.  Must match
 both /\ *linere*\ / and /\ *goodre*\ /.
 


- keep
 
 Specifies which matching lines should be kept.
 
 
 - ``first``
  
  Keep only the first line matching /\ *linere*\ /.
  
 
 
 - ``last``
  
  Keep only the last line matching /\ *linere*\ /.
  
 
 
 - ``all``
  
  Default: keep all lines matching /\ *linere*\ /.
  
 
 


- add
 
 If no match for /\ *linere*\ / is found, ``NCM::Check::lines`` may add the line to
 the file.  This option specifies where to add the line:
 
 
 - ``first``
  
  Add \ *good*\  string as the first line of the file.
  
 
 
 - ``last``
  
  Default: add \ *good*\  string as the last line of the file.
  
 
 
 - ``no``
  
  Do not alter the file.
  
 
 


- backup
 
 Save a copy of the original file, appending \ *suffix*\  to the filename.
 


- noaction
 
 Override the global $NoAction flag.
 



