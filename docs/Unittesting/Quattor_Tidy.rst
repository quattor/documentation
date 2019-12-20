
##############
Quattor\::Tidy
##############


****
NAME
****


Test::Quattor::Tidy - Run perltidy.


***********
DESCRIPTION
***********


This is a class to run perltidy on code with tidy options.

The tidy options are in the perltidy manpage
    man perltidy


*******
METHODS
*******



- new
 
 
 - codedirs
  
  An arrayref of paths to look for perl code (uses ``Test::Pod::all_pod_files``).
  
  Default is ``target/lib/perl``.
  
 
 


- check
 
 Run perltidy on filename
 


- test
 
 Run critic test on all files found with ``all_pod_files`` in all codedirs.
 


