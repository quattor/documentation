
#####################################
NCM\::Component\::Systemd\::Systemctl
#####################################


****
NAME
****


NCM::Component::Systemd::Systemctl handle all systemd
interaction via ``systemctl`` command.

Public methods
==============



- systemctl_show
 
 ``logger`` is a mandatory logger to pass.
 
 Run ``systemctl show`` on single ``$unit`` and return parsed output.
 If ``$unit`` is undef, the manager itself is shown.
 
 Optional arguments:
 
 
 - no_error
  
  Report a failure with ``systemctl show`` with ``verbose`` level.
  If nothing is specified, an ``error`` is reported.
  
 
 
 If succesful, returns a hashreference interpreting the ``key=value`` output.
 Following keys have the value split on whitespace and a array reference
 to the result as output
 
 
 - After =item Before  =item Conflicts  =item Names  =item RequiredBy  =item Requires  =item TriggeredBy  =item Triggers  =item WantedBy  =item Wants
 
 
 
 Returns undef on failure.
 


- systemctl_daemon_reload
 
 ``logger`` is a mandatory logger to pass.
 
 Reload systemd manager configuration (e.g. when units have been modified).
 
 Returns undef on failure, SUCCESS otherwise.
 


- systemctl_list_units
 
 ``logger`` is a mandatory logger to pass.
 
 Return a hashreference with all units and their details for ``type``.
 ``type`` is passed to the ``systemctl_list`` method.
 


- systemctl_list_unit_files
 
 ``logger`` is a mandatory logger to pass.
 
 Return a hashreference with all unit-files and their details for ``type``.
 ``type`` is passed to the ``systemctl_list`` method.
 


- systemctl_list_deps
 
 ``logger`` is a mandatory logger to pass.
 
 Return a hashreference with all dependencies
 (i.e. required and wanted units) of the specified ``unit``
 flattened. (This includes the unit itself).
 
 If ``reverse`` is set to true (default is false), it returns
  the revese dependencies (i.e. units with dependencies of
  type Wants or Requires on the given unit).
 
 The keys are the full unit names, values are 1. (A hash is used
 to allow easy lookup, instead of a list).
 
 The flattening is done via the ``--plain`` option of systemctl,
 the reverse result via the ``--reverse`` option. Both options
 are available since systemd-208 (which is in e.g. EL7).
 


- systemctl_command_units
 
 Run the systemctl ``command`` for ``units``.
 
 An error is logged when the exitcode is non-zero.
 
 Returns exitcode and output.
 


- systemctl_is_enabled
 
 Run ``systemctl is-enabled`` for ``unit``.
 
 Returns output without trailing newlines on success.
 Undef returned (no error reported) when the exitcode is non-zero.
 


- systemctl_is_active
 
 Run ``systemctl is-active`` for ``unit``.
 
 Returns output without trailing newlines on success.
 Undef returned (no error reported) when the exitcode is non-zero.
 



Private methods
===============



- systemctl_list
 
 Helper method to generate and parse output from ``systemctl list-...`` commands like
 ``list-units`` or ``list-unit-files``.
 
 ``logger`` is a mandatory logger to pass.
 
 ``spec`` is translated in the ``list-<spec``> command, ``regexp`` is the named
 regular expression that is used to match the output.
 
 ``type`` is the type filter (if defined).
 
 The regexp must have a ``name`` named group, its value is used for the keys of the
 hashref that is returned.
 Output that does not match the regexp is skipped, if the regexp matches but
 there is no ``name`` value in the named group, it is also skipped and
 logged as error.
 


- systemctl_simple_command
 
 Run a simple systemctl command (like is-active, is-enabled etc.).
 
 Returns output without trailing newlines on success, undef otherwise.
 