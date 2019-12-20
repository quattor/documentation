
#################################
Quattor\::TextRender\::RegexpTest
#################################


****
NAME
****


Test::Quattor::TextRender::RegexpTest - Class to handle a single regexptest
and the input text is rendered rather then passed.


***********
DESCRIPTION
***********


This class parses and executes the tests as described in a single regexptest.
It inherits from Test::Quattor::RegexpTest with main difference that the
text to test is rendered rather then passsed.

Public methods
==============



- new
 
 Returns a new object, accepts the following options
 
 
 - regexp
  
  The regexptest file.
  
 
 
 - config
  
  The configuration instance to retreive the values from.
  
 
 
 - ttincludepath
  
  The includepath for CCM::TextRender.
  
 
 
 - ttrelpath
  
  The relpath for CCM::TextRender.
  
 
 



