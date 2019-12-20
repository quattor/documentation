
###############################################
NCM\::Component\::Systemd\::Service\::Chkconfig
###############################################


****
NAME
****


NCM::Component::Systemd::Service::Chkconfig is a class handling services
that can be controlled via (older) ``ncm-chkconfig``.

Public methods
==============



- new
 
 Returns a new object, accepts the following options
 
 
 - log
  
  A logger instance (compatible with ``CAF::Object``).
  
 
 


- current_units
 
 Return hash reference with current configured units
 determined via ``chkconfig --list``.
 
 (No type to specify, ``sysv`` type is forced).
 


- current_target
 
 Return the current target based on legacy ``current_runlevel``.
 


- default_target
 
 Return the default target based on legacy ``default_runlevel``.
 


- configured_units
 
 ``configured_units`` parses the ``tree`` hash reference and builds up the
 units to be configured. It returns a hash reference with key the unit name and
 values the details of the unit.
 
 (``tree`` is typically ``$config->getElement('/software/components/chkconfig/service')->getTree``.)
 
 This method converts the legacy states as following
 
 
 - del : masked
 
 
 
 - add: disabled
 
 
 
 - off : disabled
 
 
 
 - on : enabled
 
 
 
 - reset: this state is ignored / not supported.
 
 
 



Private methods
===============



- is_possible_missing
 
 Determine if ``unit`` is ``possible_missing``
 (see ``make_cache_alias``). (Returns 0 or 1).
 
 A unit is possible_missing if
 
 
 - the unit is in state masked or disabled (i.e. unit that is not expected to be running anyway).
  
  Other then pure systemd, chkconfig state off always implies
  that a disabled service unit is not running.
  
 
 


- generate_runlevel2target
 
 Create, set and return the ``runlevel2target`` map
 (will reset existing one, return is merely for testing).
 


- convert_runlevels
 
 Convert the ``ncm-chkconfig`` levels to new systemsctl targets
 
 ``legacylevel`` is a string with integers e.g. "234".
 Retrun a array reference with the targets.
 


- default_runlevel
 
 ``default_runlevel`` returns the default runlevel
 via the INITTAB file. If that fails, the default
 DEFAULT_RUNLEVEL is returned.
 


- current_runlevel
 
 Return the current legacy runlevel.
 
 The rulevel is determined by trying (in order)
 ``/sbin/runlevel`` or ``who -r``. If both fail, the
 ``default_runlevel`` method is called and its value
 is returned.
 



