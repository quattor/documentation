
################
CAF\::FileReader
################


****
NAME
****


CAF::FileReader - Class for only reading files in CAF applications.


***********
DESCRIPTION
***********


Normal use:


.. code-block:: perl

   use CAF::FileReader;
   my $fh = CAF::FileReader->open ("my/path");
   while (my $line = <$fh>) {
      # Do something
   }


This class should be used whenever a file is to be opened for reading,
and no modifications are expected.

Printing to this file is allowed, but changes will be discarded (in
effect, the ``FileEditor`` is ``cancel``-ed.


- new
 
 Create a new instance: open the file ``$fn``, read it,
 seek to the beginning and ``cancel`` any (future) changes.
 


- open
 
 Synonym for ``new()``
 


