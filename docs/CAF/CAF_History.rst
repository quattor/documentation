
#############
CAF\::History
#############


****
NAME
****


``CAF::History`` - Class to keep history of events


********
SYNOPSIS
********



.. code-block:: perl

     package mypackage;
 
     use qw(CAF::History);
 
     sub _initialize
     {
         ...
         $self->{HISTORY} = CAF::History->new();
         ...
     }
 
     sub foo {
         my ($self, $a, $b, $c) = @_;
         ...
         $self->{HISTORY}->event();
         ...
     }



***********
DESCRIPTION
***********


``CAF::History`` provides class methods for tracking and
lookup of events.

TODO: ``CAF::History`` should provide interfaces for


- loading / saving history to file e.g. sqlite



- lookup / querying events (e.g. what files where last written to by component X)



Public methods
==============



- new
 
 Create a ``CAF::History`` instance,
 
 The history is a hashref with keys
 
 
 - ``$EVENTS``
  
  an array reference holding all events.
  
 
 
 - ``$LAST``
  
  The latest state of each id
  
 
 
 - ``$NEXTIDX``
  
  The index of the next event.
  
 
 
 - optional ``$INSTANCES``
  
  If ``keep_instances`` is set, an INSTANCES attribute is also added,
  and any events will keep track of the (blessed) instances.
  
  Caveat: this will prevent code that relies on instances going out
  of scope to perform certain actions on DESTROY, to function properly.
  
  By default, INSTANCES are not kept.
  
 
 


- event
 
 Add an event. An event is specified by an id from the ``$obj``
 and a hash ``metadata``. (Metadata can be passed as
 ``->event($obj, modified => 0);``.)
 
 If an instance is passed, the ``Scalar::Util::refaddr`` is used as internal
 identifier. If a scalar is passed, it's value is used.
 
 Object instances are also added to an instances hash-ref to handle DESTROY properly
 (but only if the initial HISTORY attribute has an INSTANCES attribute).
 
 Following metadata is added automatically
 
 
 - ``IDX``
  
  The unique event index, increases one per event.
  
 
 
 - ``ID``
  
  The identifier
  
 
 
 - ``REF``
  
  The obj ``ref``
  
 
 
 - ``TS``
  
  The timestamp (private method ``_now`` is used to determine the timestamp)
  
 
 
 The last metadata of each event is also held stored (for convenient access).
 
 Returns SUCCESS on success, undef otherwise.
 


- query_raw
 
 Primitive interface to query the events.
 
 ``match`` is a anonymous sub that is passed
 the event as (only) argument
 (each event is a metadata hashref).
 Returns true if the event matches and is to be returned.
 
 ``filter`` is an arrayref of metadata keys to filter from the event
 (only event metadata matching the filter is returned).
 
 Returns an arrayref of (a shallow copy of) the event metadata.
 
 TODO: support proper, human-friendly query interface via (NO)SQL
 


- close
 
 Closes the history which triggers following
 
 
 - destroy INSTANCES
 
 
 
 - TODO: report an overview of events
  
  E.g. all modified FileWriter and Editors
  
 
 
 Returns SUCCESS on success, undef otherwise.
 



Private methods
===============



- _now
 
 Return the timestamp to use. Implemented using builtin ``time`` for now,
 i.e. no timezones.
 


- _cleanup_instances
 
 Cleanup instances and remove any reference
 to instances held by the history.
 
 This might trigger new events.
 After all, we must make sure we have all the events.
 
 Following methods are supported
 
 
 - ``close``
  
  If the instance has a ``close`` method, the method is
  called without any arguments.
  
 
 
 Returns SUCCESS on success, undef otherwise.
 



