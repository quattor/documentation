
####################
Quattor\::TextRender
####################


****
NAME
****


Test::Quattor::TextRender - Class for unittesting
the TextRender templates.


***********
DESCRIPTION
***********


This class should be used whenever to unittest templates
that can be processed via TextRender. (For testing ncm-metaconfig
templates looked at the derived Test::Quattor::TextRender::Metaconfig
class).

Public methods
==============



- new
 
 Returns a new object, accepts the following options
 
 
 - basepath
  
  Basepath that points to the templates.
  
 
 
 - ttpath
  
  Path to the TT files.
  If the path is not absolute, search from basepath.
  
 
 
 - panpath
  
  Path to the (mandatory) pan templates.
  If the path is not absolute, search from basepath.
  
 
 
 - pannamespace
  
  Namespace for the (mandatory) pan templates. (Use empty
  string for no namespace).
  
 
 
 - namespacepath
  
  Destination directory to create a copy of the pan templates
  in correct namespaced directory. Relative paths are assumed
  relative to the current working directory.
  
  If no value is set, a random directory will be used.
  
 
 
 - panunfold
  
  Boolean to force or disable the "unfolding" of the pan templates
  in the namespacepath with correct pannamespace. Default is true.
  
  The ``make_namespace`` method  takes care of the actual unfolding (if any).
  
 
 
 - expect
  
  Expect is a hash reference to bypass some built-in tests
  in the test methods.
  
  Use with care, better to fix the actual problem.
  (No attempt is made to make this any userfriendly;
  main reason of existence is to unittest
  these test modules).
  
 
 
 - invalidtt
  
  Array reference of invalid TT files to pass the ``test_gather_tt`` test method.
  
 
 
 - invalidpan
  
  Array reference of invalid pan templates to pass the ``test_gather_pan`` test method.
  
 
 



gather_tt
=========


Walk the ``ttpath`` and gather all TT files
A TT file is a text file with an ``.tt`` extension;
they are considered 'invalid' when they are
in a 'test' or 'pan' directory or
when they fail syntax validation.

Returns an arrayreference with path
(relative to the basepath) of TT and invalid TT files.


test_gather_tt
==============


Run tests based on gather_tt results; returns nothing.


gather_pan
==========


Same as Test::Quattor::Object ``gather_pan``, but with <relpath> set
to the instance 'basepath'. (With ``panpath`` and ``pannamespace`` as arguments)


make_namespace
==============


Create a copy of the gathered pan files from ``panpath`` in the correct ``pannamespace``.
Directory structure is build up starting from the instance ``namespacepath`` value.

Returns an arrayreference with the copy locations.

If the ``panunfold`` attribute is true, a copy of the pan templates is placed
in the expected subdirectory under the ``namespacepath``.
If ``panunfold`` attribute is false, the pan templates are assumed to be in the
correct location, and nothing is done.


test_gather_pan
===============


Run tests based on gather_pan results; returns nothing.

(``panpath`` and ``pannamespace`` can be passed as arguments to
override the instance values).


