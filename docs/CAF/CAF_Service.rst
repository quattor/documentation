
#############
CAF\::Service
#############


****
NAME
****


CAF::Service - Class for starting and stopping daemons in different
platforms


********
SYNOPSIS
********



.. code-block:: perl

     use CAF::Service;
     my $srv = CAF::Service->new(['ntpd'], log => $self, %opts);
     $srv->reload();
     $srv->stop();
     $srv->start();
     $srv->restart();
     $srv->stop_sleep_start();


Will do the right thing with SystemV Init scripts, Systemd units and
Solaris' ``svcadm``.


***********
DESCRIPTION
***********


This class abstracts away the differences when operating with Daemons
in different Unixes.

Private methods
===============



- ``_initialize``
 
 Initialize the process object. Arguments:
 
 
 - ``$services``
  
  Reference to a list of services to be handled.
  
 
 
 It takes some extra optional arguments:
 
 
 - ``log``
  
  A ``CAF::Reporter`` object to log daemon activities to.
  
 
 
 - ``timeout``
  
  Maximum execution time, in seconds, for any service operations. If
  it's too slow it will be killed.  If not defined, the command won't
  time out.
  
  On Solaris it implies that ``svcadm`` actions are executed
  synchronously.  After this timeout, the operation will continue in
  background, but will NOT mark the service as failed.  For marking
  timed out services operations as failed, we have to edit the method
  definition, which is out of the scope of this method.  See the man
  page for smf_method for more details.
  
  On systemd-based systems, the timeout parameter is ignored.  The
  correct way to handle timeouts in systemd is to store them in the unit
  file, which will ensure they are respected in any context that unit
  may be called.
  
 
 
 - ``sleep``.
  
  Used only in ``stop_sleep_start``. Determines the number of
  seconds to sleep after ``stop`` before proceeding with ``start``.
  
 
 
 - ``persistent``
  
  Used only in the Solaris variant of ``start`` and ``stop``.  Make the
  enabling or disabling of this service persist in subsequent reboots.
  Implies not passing the ``-t`` flag to ``svcadm``.
  
 
 
 - ``recursive``.
  
  Used only in the Solaris variant of ``start`` and ``stop``.  Starts or
  stops all the dependencies for the given daemons, too.
  
 
 
 - ``synchronous``
  
  Used only in the Solaris variant of ``restart``.  Waits until all
  services have been restarted.
  
  If no ``timeout`` was passed, it will wait forever.
  
 
 
 ...
 



Public methods
==============



- ``restart``
 
 Restarts the daemons.
 


- ``start``
 
 Starts the daemons.
 


- ``stop``
 
 Stops the daemons
 


- ``reload``
 
 Reloads the daemons
 


- ``stop_sleep_start``
 
 Stops the daemon, sleep, and then start the dameon again.
 Only when both ``stop`` and ``start`` are successful, return success.
 


- os_flavour
 
 Determine and return the OS flavour (/variant)
 
 Current flavours are
 
 
 - linux_sysv
  
  Linux OS with SysV int system
  
 
 
 - linux_systemd
  
  Linux OS with systemd
  
 
 
 - solaris
  
  Solaris OS
  
 
 
 (All supported flavours are exported via ``@FLAVOURS``.)
 



Private methods
===============



- __make_method
 
 A generator for service methods, to be used in e.g.
 subclassing. In the example below we create a custom service
 class that supports e.g. 'service myservice init':
 
 
 .. code-block:: perl
 
      package MyService;
  
      use CAF::Service qw(__make_method @FLAVOURS);
      use parent qw(CAF::Service);
  
      sub _initialize {
          my ($self, %opts) = @_;
          return $self->SUPER::_initialize(['myservice'], %opts);
      }
  
      my $method = 'init';
      foreach my $flavour (@FLAVOURS) {
          no strict 'refs';
          *{"${method}_${flavour}"} = __make_method($method, $flavour);
          use strict 'refs';
      }
  
      1;
 
 
 This class can than be used in the same way as ``CAF::Service``
 
 
 .. code-block:: perl
 
      use MyService;
      ...
      my $serv = MyService->new();
      $serv->init();
      ...
      $serv->reload();
 
 



