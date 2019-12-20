
####################
CAF\::ServiceActions
####################


****
NAME
****


CAF::ServiceActions - Class for running different ``CAF::Service`` actions
on groups of daemons.


********
SYNOPSIS
********



.. code-block:: perl

     use CAF::ServiceActions;
 
     # short
     CAF::ServiceActions->new(log => $self, pairs => {daemon1 => 'start', 'daemon2' => 'reload'})->run();
 
     # long
     my $srvact = CAF::ServiceActions->new(log => $self);
     ...
     $srvact->add({daemon1 => 'restart', daemon2 => 'reload'});
     ...
     $srvact->add({daemon3 => 'restart'}, msg => 'for file XYZ');
     ...
     $srvact->run();



***********
DESCRIPTION
***********


This class can be used to run different ``CAF::Service`` actions
on groups of daemons.

Private methods
===============



- ``_initialize``
 
 Initialize the object.
 It takes optional arguments:
 
 
 - ``log``
  
  A ``CAF::Reporter`` object to log daemon activities to.
  
 
 
 - ``pairs``
  
  Daemon/action pairs (in hashref) passed to ``add`` method.
  
 
 
 All other named options are passed to ``add`` method if the ``pairs`` option is passed.
 


- ``add``
 
 Add daemon/action ``pairs`` as hashref, e.g.
 
 
 .. code-block:: perl
 
      $srvact->add({daemon1 => 'restart', daemon2 => 'stop'});
 
 
 Does not run any service action (see ``run`` method).
 
 It takes optional arguments:
 
 
 - ``msg``
  
  A string that is appended to the log messages.
  
 
 
 Returns SUCCESS on success, undef otherwise.
 


- ``run``
 
 Run the actions for all daemons.
 



