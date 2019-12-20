
#########
CAF\::Log
#########


****
NAME
****


CAF::Log - Simple class for handling log files


********
SYNOPSIS
********



.. code-block:: perl

   use CAF::Log;
 
   my $log = CAF::Log->new('/foo/bar', 'at');
 
   $log->print("this goes to the log file\n");
   $log->close();



***********
DESCRIPTION
***********


The \ **CAF::Log**\  class allows to instantiate objects for writing log files.
A log file line can be prefixed by a time stamp.

Public methods
==============



- ``close()``: boolean
 
 closes the log file, returns SUCCESS on success, undef otherwise
 (if no FH attribute exists).
 


- ``print($msg)``: boolean
 
 Prints ``$msg`` into the log file.
 
 If ``PROCID`` attribute is defined (value is irrelevant),
 the proces id in square brackets (``[PID]``) and additional
 space are prepended.
 
 If ``TSTAMP`` attribute is defined (value is irrelevant),
 a ``YYYY/MM/DD-HH:mm:ss`` timestamp and additional space
 are prepended.
 
 No newline is added to the message.
 
 Returns the return value of invocation of FH print method.
 



Private methods
===============



- ``_initialize($filename, $options)``
 
 ``$options`` is a string with magic letters
 
 
 - a: append to a logfile
 
 
 
 - w: truncate a logfile
 
 
 
 - t: generate a timestamp on every print
 
 
 
 - p: add PID
 
 
 
 Only one of ``w`` or ``a`` can and has to be set. (There is no default.)
 
 If the ``w`` option is used and there was a previous
 log file, it is renamed with the extension '.prev'.
 
 Examples:
 
 
 .. code-block:: perl
 
      CAF::Log->new('/foo/bar', 'at'): append, enable timestamp
      CAF::Log->new('/foo/bar', 'w') : truncate logfile, no timestamp
 
 
 If the filename ends with ``.log``, the ``SYSLOG`` attribute is set to
 basename of the file without suffix (relevant for ``CAF::Reporter::syslog``).
 


- DESTROY
 
 Called during garbage collection. Invokes close().
 



