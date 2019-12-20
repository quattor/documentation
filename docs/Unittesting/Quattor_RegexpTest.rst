
####################
Quattor\::RegexpTest
####################


****
NAME
****


Test::Quattor::RegexpTest - Class to handle a single regexptest.


***********
DESCRIPTION
***********


This class parses and executes the tests as described in a single regexptest.

Public methods
==============



- new
 
 Returns a new object, accepts the following options
 
 
 - regexp
  
  The regexptest file.
  
 
 
 - text
  
  The text to test.
  
 
 



parse
=====


Parse the regexp file in 3 sections: description, flags and tests.

Each section is converted in an instance attribute named 'description',
'flags' and 'tests'.


parse_description
=================


Parse the description block and set the description attribute.

First argument ``blocktxt`` is the 1st block of the regexptest file.


parse_flags
===========


Parse the flags block and set ``flags`` attribute

Following flags are supported


- regular expression flags:
 
 
 - multiline
  
  (no)multiline / multiline=1/0
  
 
 
 - singleline
  
  singleline / singleline=1/0
  
  (This flag can coexist with multiline)
  
 
 
 - extended format
  
  extended / extended=1/0
  
 
 
 - case senistive
  
  case(in)sensistive / casesensitive = 0/1
  
 
 


- order flag
 
 
 - ordered matches
  
  (un)ordered / ordered=0/1
  
 
 


- negate
 
 negate / negate = 0/1
 
 Negate all regexps, none of the regexps can match
 (is an alias for ``COUNT 0`` on every regtest;
 overwritten when COUNT is set for individual regexp)
 


- quote
 
 quote / quote = 0/1
 
 Whole tests block is 1 regular expression. With ``quote`` flag set,
 ``multiline`` flag is logged and ignored; ``ordered`` flag is
 meaningless (and silently ignored).
 


- location of module and contents settings:
 
 
 - metaconfigservice=/some/path
  
  Also any flag starting with ``/`` is interpreted as ``metaconfigservice``
  
 
 
 - renderpath=/some/path
  
  Also any flag starting with ``//`` is interpreted as ``renderpath``
  
 
 
 - rendermodule
  
  Specify the value of the module to use. (Precedes
  metaconfigservice/renderpath value).
  
 
 
 - contentspath
  
  Specify the path to use for contents. (Precedes
  metaconfigservice/renderpath value).
  
 
 
 - element
  
  Comma separated list of predefined element convert options for CCM::TextRender.
  
 
 


- Default settings
 
 
 .. code-block:: perl
 
      ordered=1
      multiline=1
      casesensitive=1
      renderpath=/metaconfig
 
 


First argument ``blocktxt`` is the 2nd block of the regexptest file.


parse_tests
===========


Parse the tests block and set ``tests`` attribute

If the ``quote`` flag is set, the whole tests block is
seen as one big regular expression, and rendered text
has to be an exact match, incl EOF newline etc.

Without the ``quote`` flag set, the tests are parsed line by line,
and seen as one regexp per line.

Lines starting with `` \s\*#{3}  `` (trailing space!) are comments.

Lines ending with ``\s#{3}`` are interpreted as having options set.
Supported options


- COUNT
 
 The exact number of matches is ``COUNT \d+``
 (use ``COUNT 0`` to make sure a line doesn't match).
 
 This is a global count, e.g. in ordered mode the count
 itself is not number of matches since previous test match.
 


The first argument ``blocktxt`` is the 3rd block of the regexptest file


test
====


Perform the tests as defined in the flags and specified in the 'tests' section


