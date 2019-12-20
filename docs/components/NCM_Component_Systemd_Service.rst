
###################################
NCM\::Component\::Systemd\::Service
###################################


****
NAME
****


NCM::Component::Systemd::Service handles the ``ncm-systemd`` units.

Public methods
==============



- new
 
 Returns a new object with argument ``base`` (the configuration path)
 and accepts the following options
 
 
 - log
  
  A logger instance (compatible with ``CAF::Object``).
  
 
 


- configure
 
 ``configure`` gathered the to-be-configured units from the ``config`` using the
 ``gather_units`` method and then takes appropriate actions.
 



Private methods
===============



- set_unconfigured_default
 
 Return the default behaviour for unconfigured units from ``ncn-systemd``
 and legacy ``ncm-chkconfig``.
 


- gather_configured_units
 
 Gather the list of all configured units from both ``ncm-systemd``
 and legacy ``ncm-chkconfig`` location, and take appropriate actions.
 
 For any unit defined in both ``ncm-systemd`` and ``ncm-chkconfig`` location,
 the ``ncm-systemd`` settings will be used.
 
 Returns a hash reference with key the unit name and value the unit detail.
 


- gather_current_units
 
 Gather list of current units from both ``systemctl`` and legacy ``chkconfig``
 using resp. ``unit`` and ``chkconfig`` ``current_units`` methods.
 
 The hashref ``relevant_units`` is used to run minimal set
 of system commands where possible: e.g. if the hashref represents the
 configured units and if ``unconfigured`` is ``ignore``, only gathered
 details for these units.
 


- process
 
 ``process`` the ``configured`` and ``current`` units and
 return hash references with state and activation changes.
 
 It uses the ``current`` units to make the required decisions.
 Unconfigured current units are also processed according the
 ``unconfigured`` value.
 


- change
 
 Actually make the changes as specified in
 the hashrefs ``states`` and ``acts`` (which hold the
 changes to be made to resp. the state and the activity
 of the units).
 



