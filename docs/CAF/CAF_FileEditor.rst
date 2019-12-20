
################
CAF\::FileEditor
################


****
NAME
****


CAF::FileEditor - Class for securely making minor changes in CAF
applications.


***********
DESCRIPTION
***********


This class should be used whenever a file is to be opened for
modifying its existing contents. For instance, if you want to add a
single line at the beginning or the end of the file.

As usual, all operations may be logged by passing a ``log`` argument to
the class constructor.

Public methods
==============



- new
 
 Returns a new object it accepts the same arguments as the constructor
 for ``CAF::FileWriter`` with one additional option:
 
 
 - source
  
  This option, when present, must be a file name whose contents will be used
  as the initial contents for the edited file if the source modification time
  is more recent than the edited file modification time. This allows to rebuild
  the file contents based on a new version of the reference file.
  
  The ``source`` can be a pipe: in this case, it is always considered more recent
  than the edited file.
  
 
 


- open
 
 Synonym for ``new()``
 


- set_contents
 
 Sets the contents of the file to the given argument. Usually, it
 doesn't make sense to use this method directly. Just use a
 ``CAF::FileWriter`` object instead.
 


- head_print
 
 Appends a line to the very beginning of the file.
 


- seek_begin
 
 Seek to the beginning of the file.
 


- seek_end
 
 Seek to the end of the file.
 


- replace_lines(re, goodre, newvalue)
 
 Replace any lines matching ``re`` but \*not\* ``goodre`` with
 ``newvalue``. If there is no match, nothing will be done. For instance,
 
 
 .. code-block:: perl
 
      $fh->replace(qr(hello.*), qr(hello.*world), 'hello and good bye, world!')
 
 
 Will replace all lines containing 'hello' but \ **not**\  world by the
 string 'hello and good bye, world!'. But if the file contents are
 
 
 .. code-block:: perl
 
      There was Eru, who in Arda is called Iluvatar
 
 
 it will be kept as is.
 
 This is useful when we want to change a given configuration directive
 only if it exists and it's wrong.
 
 The regular expressions can be expressed with the ``qr`` operator, thus
 allowing for modification flags such as ``i``.
 


- add_or_replace_sysconfig_lines(key, value, whence)
 
 Replace the ``value`` in lines matching the ``key``. If
 there is no match, a new line will be added to the where ``whence``
 and ``offset`` tells us.
 The sysconfig_separator value can be changed if it's not the usual '='.
 


- add_or_replace_lines(re, goodre, newvalue, whence, offset, add_after_newline)
 
 Replace lines matching ``re`` but not ``goodre`` with ``newvalue``. If
 there is no match, a new line will be added where the ``whence``
 and ``offset`` tell us. See ``IO::String::seek``
 for details; e.g. use the constants tuple
 BEGINNING_OF_FILE or ENDING_OF_FILE.
 If ``add_after_newline`` is true or undef, before adding the new line,
 it is verified that a newline precedes this position. If no newline
 char is found, one is added first.
 
 ``whence`` must be one of SEEK_SET, SEEK_CUR or SEEK_END;
 everything else will be ignored (an error is logged if
 logging is set)).
 
 Reminder: if the offset position lies beyond SEEK_END, padding will
 occur with $self->pad, which defaults to ``\0``.
 


- get_all_positions(regex, whence, offset)
 
 Return reference to the arrays with the positions
 before and after all matches of the compiled regular expression
 ``regex``, starting from ``whence`` (default
 beginning) and ``offset`` (default 0). (If the regexp
 does not match, references to empty arrays are returned).
 
 Global regular expression matching is performed (i.e. ``m/$regex/g``).
 The text is searched without line-splitting, but multiline regular
 expressions like ``qr{^something.\*$}m`` can be used for per line matching.
 


- get_header_positions(regex, whence, offset)
 
 Return the position before and after the "header".
 A header is a block of lines that start with same
 compiled regular expression ``regex``.
 Default value for ``regex`` is ``qr{^\s\*#.\*$}m``
 (matching a block of text with each line starting with a ``#``);
 the default value is also used when ``regex`` is ``undef``.
 ``(-1, -1)`` is returned if no match was found.
 
 ``whence`` and ``offset`` are passed to underlying ``get_all_positions``
 call.
 


- remove_lines(re, goodre)
 
 Remove any lines matching ``re`` but \*not\* ``goodre``.
 If there is no match, nothing will be done.
 




******************
EXPORTED CONSTANTS
******************


The following constants are automatically exported when using this module:


- ``BEGINNING_OF_FILE``
 
 Flag to pass to ``add_or_replace_lines``. Lines should be added at the
 beginning of the file. (To be used in list context, as this is actually
 ``(SEEK_SET, 0)``.)
 


- ``ENDING_OF_FILE``
 
 Flag to pass to ``add_or_replace_lines``. Lines should be added at the
 end of the file. (To be used in list context, as this is actually
 ``(SEEK_END, 0)``.)
 



********
EXAMPLES
********


Appending to the end of a file
==============================


For instance, you may want to append a line to the end of a file, if
it doesn't exist already:


.. code-block:: perl

     my $fh = CAF::FileEditor->open ("/foo/bar",
                                     log => $self);
     if (${$fh->string_ref()} !~ m{hello, world}m) {
         print $fh "hello, world\n";
     }
     $fh->close();



Cancelling changes in case of error
===================================


This is a subclass of ``CAF::FileWriter``, so just do as you did with
it:


.. code-block:: perl

     my $fh = CAF::FileEditor->open ("/foo/bar",
                                     log => $self);
     $fh->cancel() if $error;
     $fh->close();



Appending a line to the beginning of the file
=============================================


Trivial: use the ``head_print`` method:


.. code-block:: perl

     my $fh = CAF::FileEditor->open ("/foo/bar",
                                     log => $self);
     $fh->head_print ("This is a nice header for my file");



Replacing configuration lines
=============================


If you want to replace existing lines:


.. code-block:: perl

     my $fh = CAF::FileEditor->open ("/foo/bar",
                                     log => $self);
     $fh->replace_lines (qr(pam_listfile),
                         qr(session\s+required\s+pam_listfile.so.*item=user),
                         join("\t", qw(session required pam_listfile.so
                                       onerr=fail item=user sense=allow
                                       file=/some/acl/file)));


This will \ **not**\  add any new lines in case there are no matches.


Adding or replacing lines
=========================


If you want to replace lines that match a given regular expression,
and have to add them to the beginning of the file in case there are no
matches:


.. code-block:: perl

     my $fh = CAF::FileEditor->open ("/foo/bar",
                                     log => $self);
     $fh->add_or_replace_lines (qr(pam_listfile),
                         qr(session\s+required\s+pam_listfile.so.*item=user),
                         join("\t", qw(session required pam_listfile.so
                                       onerr=fail item=user sense=allow
                                       file=/some/acl/file)),
                         BEGINNING_OF_FILE);




********
SEE ALSO
********


This class inherits from ``CAF::FileWriter``, and thus from
``IO::String``.

