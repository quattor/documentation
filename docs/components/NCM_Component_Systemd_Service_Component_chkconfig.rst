
###########################################################
NCM\::Component\::Systemd\::Service\::Component\::chkconfig
###########################################################


Methods
=======



- _set_name
 
 Set and return name to use for prefix to get the the standard configuration path
 for the systemd component ``</software/components/systemd``>
 (not the ``chkconfig`` one through inheritance).
 
 This allows for easier subclassing, but is not safe for component aliasing.
 


- _initialize
 
 Modify the inheritance to set the ``NAME`` attribute via ``_set_name`` method.
 


- skip
 
 Skip all but service configuration.
 


