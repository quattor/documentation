
############################
Quattor\::TextRender\::Suite
############################


****
NAME
****


Test::Quattor::TextRender::Suite - Class for a template test suite.


***********
DESCRIPTION
***********


A TextRender test suite corresponds to one or more
regexptests that are tested against the profile genereated
from one corresponding object template.

A test suite can be a combination of file (implying one regexptest, and that
file being the regexptest) and/or a directory
(one or more regexptests; each file in the directory is one
regexptest; no subdirectory structure allowed);
with the file or directory name
identical to the corresponding object template.

The names cannot start with a '.'.


***
new
***


Support options


- testspath
 
 Basepath for the suite tests.
 


- regexps
 
 Path to the suite regexptests  (``testspath```/regexps` is default when not specified).
 


- profiles
 
 Path to the suite object templates (``testspath```/profiles` is default when not specified).
 


- ttincludepath
 
 Includepath to use for CAF::TextRender.
 


- ttrelpath
 
 relpath to use for CAF::TextRender.
 


- filter
 
 A compiled regular expression that is used to filter the found regexptest files
 (matching relative filenames are kept; non-matcing ones are removed).
 
 One can also set the ``QUATTOR_TEST_SUITE_FILTER`` enviroment variable, which will be
 used as regular expression pattern for the filter.
 


gather_regexp
=============


Find all regexptests. Files/directories that start with a '.' are ignored.

Returns hash ref with name as key and array ref of the regexptests paths.


gather_profile
==============


Create a hash reference of all object templates in the 'profilespath'
with name key and filepath as value.


one_test
========


Run all regexptest ``$regexps`` for a single test profile ``profile`` with name ``name``.


test
====


Run all tests to validate the suite.


