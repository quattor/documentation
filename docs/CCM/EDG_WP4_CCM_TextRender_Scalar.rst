
#####################################
EDG\::WP4\::CCM\::TextRender\::Scalar
#####################################


****
NAME
****



.. code-block:: perl

     CCM::TextRender::Scalar - Class to access scalar/property Element attributes within TT.



***********
DESCRIPTION
***********


This is a wrapper class to access some scalar/property Element attributes
(in particular the type) within TT.

Methods
=======



- new
 
 Create a new instance with ``value`` and ``type``.
 


- _stringify
 
 Method called to stringification. Simply returns the data in string context
 


- get_type
 
 Return TYPE attribute
 


- get_value
 
 Return value (i.e. the VALUE attribute)
 (can be useful in case the overloading behaves unexpected)
 


- is_boolean
 
 Return true if the TYPE is boolean
 


- is_string
 
 Return true if the TYPE is string
 


- is_double
 
 Return true if the TYPE is double
 


- is_long
 
 Return true if the TYPE is long
 



