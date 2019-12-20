
################################
Quattor\::TextRender\::Component
################################


****
NAME
****


Test::Quattor::TextRender::Component - Class for unittesting
the TextRender usage (and TT in particular) in components.


***********
DESCRIPTION
***********


This class should be used to unittest CAF::TextRender usage
in components.

To be used as


.. code-block:: perl

     my $u = Test::Quattor::TextRender::Component->new(
         component => 'openneubla',
         )->test();


The tests require access to the ``template-library-core``
repository for using standard types in the schema files.

By default, the ``template-library-core`` is expected to be in the
same directory as the one this test is being ran from.
One can also specify the location via the ``QUATTOR_TEST_TEMPLATE_LIBRARY_CORE``
environment variable.

Public methods
==============



- new
 
 Returns a new object, basepath is the default location
 for component TT files (src/main/resources).
 
 Accepts the following options
 
 
 - component
  
  The name of the component that these tests are part of.
  
 
 
 - usett
  
  Force (or disable) the TT gather and verification test. E.g. disable when a
  builtin TextRender module is used. (By default, ``usett`` is true).
  
 
 
 - pannamespace
  
  For modules that are almost components (like AII plugins), one can change the
  ``pannamespace`` (default is ``<components/<component``>>). (Use empty string to
  indicate no namespace).
  
 
 
 - skippan
  
  If ``skippan`` is true, skip all pan related tests and checks.
  This should only be needed in some rare case
  (e.g. when testing TT files in other modules like CCM).
  Default is not to skip any pan related tests.
  
 
 



