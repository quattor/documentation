
#################################
Quattor\::TextRender\::Metaconfig
#################################


****
NAME
****


Test::Quattor::TextRender::Metaconfig - Class for unittesting
the ncm-metaconfig services and their templates.


***********
DESCRIPTION
***********


This class should be used to unittest ncm-metaconfig
services and their templates.

To be used as


.. code-block:: perl

     my $u = Test::Quattor::TextRender::Metaconfig->new(
         service => 'logstash',
         version => '1.2',
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
 for metaconfig-unittests (src/main/metaconfig).
 
 Accepts the following options
 
 
 - service
  
  The name of the service (the service is a subdirectory of the basepath).
  
 
 
 - version
  
  If a specific version is to be tested (undef assumes no version).
  
 
 
 - usett
  
  Force (or disable) the TT gather and verification test. E.g. disable when a
  builtin TextRender module is used. (By default, ``usett`` is true).
  
 
 



