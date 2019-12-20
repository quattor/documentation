
##################
Quattor\::Unittest
##################


****
NAME
****


Test::Quattor::Unittest - Baseline unittest module.


***********
DESCRIPTION
***********


This is a class to trigger basic unittests.
Should be used as follows:


.. code-block:: perl

     use Test::Quattor::Unittest;


Adding the test is as simple as
    echo 'use Test::Quattor::Unittest;' > 00-tqu.t


*********
FUNCTIONS
*********



- import
 
 On import, run the tests.
 
 Pass ``notest`` to disable automatic testing
 (only useful when testing this code).
 
 Pass ``nopod`` to set the ``nopodflag`` (for ``doc`` test)
 when testing (is ignored when ``notest`` is passed).
 



*******
METHODS
*******



- new
 
 No options are required/supported
 


- read_cfg
 
 Read default config followed by optional configfile ``tqu.cfg`` and optional
 variable ``$main::TQU``.
 
 Variable can be defined in main test as follows
 
 
 .. code-block:: perl
 
      BEGIN {
          our $TQU = <<'EOF';
      ...
      EOF
      }
 
 
 Every test section has at least the ``enable`` option,
 set to true by default.
 For all other options, read the respective method
 documentation.
 


- test
 
 Run all enabled tests, in order
 


- load
 
 Run basic load test using ``use_ok`` from ``Test::More``.
 
 The module(s) can be configured or guessed.
 
 Configuration parameters
 
 
 - modules
  
  Comma separated list op module names to try to load.
  
  When specified, no guesses are made, only this list is used.
  
  If ``:`` is passed, the prefix is used.
  
  All trailing ``:`` are removed.
  
 
 
 - prefix
  
  A prefix for all modules specified in the ``modules`` option.
  
 
 


- doc
 
 Documentation tests using ``Test::Quattor::Doc``.
 
 Configuration options ``poddirs``, ``podfiles``, ``emptypoddirs``, ``panpaths`` and
 ``panout`` are parsed as comma-seperated lists
 and passed to ``Test::Quattor::Doc->new``.
 
 If the ``nopodflag`` attribute is true, and no ``emptypoddirs`` are defined,
 the ``Test::Quattor::Doc::DOC_TARGET_POD`` is set as ``emptypoddirs``.
 
 ``panpaths`` value ``NOPAN`` is special, as it disables the pan tests.
 


- tt
 
 Run TT unittests using ``Test::Quattor::TextRender::Component``.
 (This does not apply to ``metaconfig`` tests).
 
 Configuration options are passed to
 ``Test::Quattor::TextRender::Component->new``.
 
 The tests are only run if the basepath (default to ``src/main/resources``)
 exists.
 


- critic
 
 Run ``Test::Quattor::Critic``
 
 Options
 
 
 - codedirs
  
  Comma-separated list of directories to look for code to test.
  (Defaults to poddirs (from doc test) or ``target/lib/perl``).
  
 
 
 - exclude
  
  A regexp to remove policies from list of fatal policies.
  
 
 


- tidy
 
 Run ``Test::Quattor::Tidy``
 
 Options
 
 
 - codedirs
  
  Comma-separated list of directories to look for code to test.
  (Defaults to poddirs (from doc test) or ``target/lib/perl``).
  
 
 


