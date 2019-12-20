
###################
Quattor\::Filetools
###################


****
NAME
****


Test::Quattor::Filetools - Read/write files
(in case mocked FileWriter/Reader cannot be used).


*********
Functions
*********



- writefile
 
 Create file with name ``fn`` (and parent directory if needed).
 Optional second argument is the
 content of the file (default is text ``ok`` (no newline)).
 


- readfile
 
 Read the content of file ``fn`` and return it.
 


