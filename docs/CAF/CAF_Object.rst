
############
CAF\::Object
############


****
NAME
****


CAF::Object - provides basic methods for all CAF objects


********
SYNOPSIS
********



.. code-block:: perl

     use parent qw(CAF::Object ...);
     ...
     sub _initialize {
         ... initialize your package
         return SUCCESS; # Success
     }



***********
DESCRIPTION
***********


\ **CAF::Object**\  is a base class which provides basic functionality to
CAF objects.

All other CAF objects should inherit from it.

All CAF classes use this as their base class and inherit their class
constructor ``new`` from here. Sub-classes should implement all their
constructor initialisation in an ``_initialize`` method which is invoked
from this base class ``new`` constructor. Sub-classes should NOT need to
override the ``new`` class method.

The subclass ``_initialize`` method has to be implemented
and has to return a boolean value indicating if the initialisation was succesful
(e.g. use ``SUCCESS`` exported by ``CAF::Object``).
In particular, one should avoid to return the ``$self`` instance at the end of
``_initialize`` (e.g. to avoid troubles when the subclass overloads logic evaluation
(which is also possible via overloading other methods such as stringification)).

Public methods
==============



- new
 
 Creates an empty hash and bless'es it as the new class instance. All arguments are then passed
 to a ``$self->_initialize(@_)`` call.
 When ``_initialize`` returns success, the ``NoAction`` attribute is set to the value of
 ``CAF::Object::NoAction`` if it didn't exist after ``_initialize``.
 If ``_initialize`` returns failure, an error is thrown and undef returned.
 


- noAction
 
 Returns the NoAction flag value (boolean)
 



Private methods
===============



- _initialize
 
 This method must be overwritten in a derived class
 


- error, warn, info, verbose, debug, report, OK, event
 
 Convenience methods to access the log/reporter instance that might
 be passed during initialisation and set to ``$self->{log}``.
 
 (When constructing classes via multiple inheritance,
 ``CAF::Reporter`` should precede ``CAF::Object`` if you want
 to use an absolute rather than a conditional logger).
 


- fail
 
 Handle failures. Stores the error message in the ``fail`` attribute,
 logs it with ``verbose`` and returns undef.
 
 To be used in subclasses that are not supposed to log/report
 any errors themself when a problem or failure occurs.
 In such classes, all failures should use ``return $self->fail("message");``.
 


- update_env
 
 Update the hashref ``$env`` with key/value
 from the ``ENV`` attribute hashref.
 (A undef value will remove the key.)
 
 Returns the ``env`` hashref.
 
 To be used as
 
 
 .. code-block:: perl
 
      # Setup local environment
      local %ENV = %ENV;
      $self->update_env(\%ENV);
 
 
 Example:
 
 
 .. code-block:: perl
 
      # some method_1 that prepares a shared environment
      sub method_1
      {
          ...
          # Prepare enviroment modifications
          $self->{ENV}->{PATH} = "/some/new/path:$ENV{PATH}";
          ...
      }
  
  
      sub do_something
      {
         ...
         # Setup local environment
         local %ENV = %ENV;
         $self->update_env(\%ENV);
  
         # everything in the remainder of the method runs in modified environment
         # is limited to the scope of this method due to 'local'
         ...
      }
 
 



