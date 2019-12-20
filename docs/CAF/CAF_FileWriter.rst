
################
CAF\::FileWriter
################


****
NAME
****


CAF::FileWriter - Class for securely writing to files in CAF
applications.


********
SYNOPSIS
********


Normal use:


.. code-block:: perl

     use CAF::FileWriter;
     my $fh = CAF::FileWriter->open ("my/path");
     print $fh "My text";
     $fh->close();


Aborting changes:


.. code-block:: perl

     use CAF::FileWriter;
     my $fh = CAF::FileWriter->open ("my/path");
     print $fh, "My text";
     $fh->cancel();
     $fh->close();



***********
DESCRIPTION
***********


This class should be used whenever a file is to be opened for writing.

If the file already exists and the printed contents are the same as
the contents present on disk, the actual file won't be modified. This
way, timestamps will be kept.

It also provides a secure way of opening files, avoiding symlink
attacks.

In case of errors, changes can be cancelled, and nothing will happen
to disk.

Finally, the file names to be handled will be logged at the verbose
level.

Gory details
============


This is a wrapper class for ``IO::String`` with customised close based on
``File::AtomicWrite``.


Public methods
==============



- new
 
 Returns a new object. It accepts the file name as its first argument,
 and the next hash as additional options:
 
 
 - ``log``
  
  The log object. If not supplied, no logging will be performed.
  
 
 
 - ``owner``
  
  UID for the file.
  
 
 
 - ``group``
  
  File's GID.
  
 
 
 - ``mode``
  
  File's permissions.
  
 
 
 - ``mtime``
  
  File's modification time.
  
 
 
 - ``backup``
  
  Create a backup file when the file already exists and will be modified.
  The value is used as a suffix to create the backup filename
  (e.g. ``.old``).
  
 
 
 - ``keeps_state``
  
  A boolean specifying whether a file change respects the current system
  state or not. A file with ``keeps_state`` will be created/modified,
  regardless of any value for ``NoAction``.
  This is useful when creating temporary files that are required for a NoAction run.
  
  By default, file changes modify the state and thus ``keeps_state`` is
  false.
  
 
 
 - ``sensitive``
  
  A boolean specifying whether a file contains sensitive information
  (like passwords). When the content of the file is modified, the changes
  (either the diff or the whole content in case of a new file) themself
  are not reported and not added to the event history.
  
 
 


- open
 
 Synonym for ``new()``
 


- close
 
 Closes the file.
 
 If the file has been saved (e.g. previous ``close`` or ``cancel``)
 nothing happens and undef is returned.
 
 If the file has not been saved,
 it checks its contents and perhaps re-writes it, in a
 secure way (not following symlinks, etc). The (re)write only occurs
 if there was a change in content and this change (or not) is
 always determined and returned, even if ``NoAction`` is true
 (but in that case nothing is (re)written).
 
 Under a verbose level, it will show in the standard output a diff of
 the old and the newly-generated contents for this file before actually
 saving to disk.
 


- cancel
 
 Marks the printed contents as invalid. The existing file will not be
 altered.
 
 Option ``msg`` to add custom message to verbose reporting.
 


- noAction
 
 Returns the NoAction flag value (boolean)
 


- stringify
 
 Returns a string with the contents of the file, so far. It overloads
 ``""``, so it's now possible to do ``$fh`` and get the contents of the
 file so far.
 
 (Returns empty string on an already closed file.)
 


- error, warn, info, verbose, debug, report, log, OK
 
 Convenience methods to access the log/reporter instance that might
 be passed during initialisation and set to ``\*$self->{LOG}``.
 


- is_verbose
 
 Determine if the reporter level is verbose.
 If it can't be determined from the reporter instance,
 use the global ``CAF::Reporter`` state.
 
 Supports boolean option ``verbose_logfile`` to check if
 reporting to logfile is verbose.
 


- event
 
 Method to track an event via LOG ``CAF::History`` instance (if any).
 
 Following metadata is added
 
 
 - filename
  
  Adds the filename as metadata
  
 
 



Private methods
===============



- _read_contents
 
 Read the contents from file ``filename`` using ``LC::File::file_contents``
 and return it.
 
 Optional named arguments
 
 
 - event
  
  A hashref that will be updated in place if an error occured. The ``error``
  attribute is set to the exception text.
  
 
 
 - missing_ok
  
  When true and ``LC::File::file_contents`` fails with ``ENOENT``
  (i.e. when ``filename`` is missing),
  the exception is ignored and no warning is reported.
  
 
 
 By default, a warning is reported in case of an error and the exception is (re)thrown.
 


- DESTROY
 
 Class destructor. Closes the file, perhaps saving it to disk.
 




********
EXAMPLES
********


Opening `/etc/sudoers`
======================


This a part of what \ *ncm-sudo*\  should do, if it used this module:


.. code-block:: perl

     my $fh = CAF::FileWriter->open ("/etc/sudoers", mode => 0440,
                                     log => $self);
     print $fh "User_Alias\t$_\n" foreach @{$aliases->{USER_ALIASES()}};
     print $fh "Runas_Alias\t$_\n" foreach @{$aliases->{RUNAS_ALIASES()}};
     ...
     $fh->close();


Which is actually simpler and safer than current code.


Specifying owner and group
==========================


Owner and group are set at the time of creating the object:


.. code-block:: perl

     my $fh = CAF::FileWriter->open ("/some/file",
                                     owner => 100
                                     group => 200);
     print $fh "Hello, world!\n";
     # I don't like what I did, just drop the changes:
     $fh->cancel();
     $fh->close();



Changing the default filehandle
===============================


If you don't want ``STDOUT`` as your default filehandle, you can just
``select`` a ``CAF::FileWriter`` object:


.. code-block:: perl

     my $fh = CAF::FileWriter->open ("/some/file",
                                     owner => 100,
                                     group => 200);
     select ($fh);
     print "Hello, world!\n";
     $fh->close();
     select (STDOUT);



Using here-documents
====================


You can use them, as always:


.. code-block:: perl

     my $fh = CAF::FileWriter->open ("/some/file");
     print $fh <<EOF
     Hello, World!
     EOF
     $fh->close();



Closing when destroying
=======================


If you forget to explictly close the ``CAF::FileWriter`` object, it
will be closed automatically when it is destroyed:


.. code-block:: perl

     my $fh = CAF::FileWriter->open ("/some/file");
     print $fh "Hello, world!\n";
     undef $fh;




********
SEE ALSO
********


This package inherits from ``IO::String``. Check its man page to
do powerful things with the already printed contents.
