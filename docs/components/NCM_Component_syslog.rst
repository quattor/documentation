
########################
NCM\::Component\::syslog
########################


****
NAME
****


``NCM::Component::syslog`` configures entries in `/etc`/(r)syslog.conf


*******
Methods
*******



- sysconfig
 
 Modify/add ``SYSLOGD`` and/or ``KLOGD`` options
 in the ``$sysconfig`` file.
 
 Returns if file changed.
 


- render
 
 Create the complete (r)syslog config file.
 
 This method is used when ``fullcontrol`` is enabled.
 
 Returns if file changed.
 


- edit
 
 Edit the (r)syslog config file, leaving entries from
 other sources intact.
 
 This method is used when ``fullcontrol`` is disabled.
 
 Returns if file changed.
 


