
#########
NCD\::CLI
#########


*************
NAME NCD::CLI
*************


Module for the ncm-ncd CLI script


*********
FUNCTIONS
*********



- app_options
 
 Extend ``CAF::Application`` options
 


- setLockCCMConfig
 
 Set ``CACHEMGR`` attribute with `EDG::WP4::CCM::CacheManager <http://search.cpan.org/search?query=EDG%3a%3aWP4%3a%3aCCM%3a%3aCacheManager&mode=module>`_ from ``cacheroot`` and
 ``CCM_CONFIG`` attribute with locked configuration with ``profileID``.
 
 Return SUCCESS on success, undef otherwise.
 


- getCCMConfig
 
 Return the CCM configuration instance from the ``CCM_CONFIG`` atribute
 (set by ``setLockCCMConfig`` method).
 


- lock
 
 Try to take the lock for the ``ncm-ncd`` application.
 Lock instance is set in ``LOCK`` attribute.
 
 Return SUCCESS on success, undef otherwise.
 


- finish
 
 Release the lock (if this instance has it)
 and exit with ``ret`` exitcode.
 


- _initialize
 
 Initialize the ``CAF::Application``
 


- check_noquattor
 
 Handle the presence of the `/etc/noquattor` file.
 Exits, does not return anything.
 


- check_options
 
 Check for any conflicting options.
 
 Exits on any conflict, does not return anything.
 


- action
 
 Take action: list, unconfigure or (default) configure.
 
 Report the components with ``list`` and exit.
 Otherwise return a hashref and the action name.
 
 Takes existing exception context as argument.
 


- report_exit
 
 Given the result of the ``NCD::ComponentProxyList`` action,
 report the succes and/or any errors and warnings and
 ``exit`` with the appropriate exitcode.
 
 Takes a second argument ``action`` to create appropriate message.
 


- main
 
 The CLI main method
 


