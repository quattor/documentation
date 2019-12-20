
##################
CAF\::ReporterMany
##################


****
NAME
****


CAF::ReporterMany - Class for console & log message reporting in CAF applications,
which allows more than one object instance each with its own reporting setup.


***********
DESCRIPTION
***********


``CAF::ReporterMany`` provides class methods for message reporting
just like ``CAF::Reporter`` does, with the main distinction that
multiple instances do not share the reporter setup
(e.g. they can each have their own debuglevel).

