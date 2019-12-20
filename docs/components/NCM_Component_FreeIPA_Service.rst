
###################################
NCM\::Component\::FreeIPA\::Service
###################################


****
NAME
****


NCM::Component::FreeIPA::Service adds service related methods to
`NCM::Component::FreeIPA::Client <http://search.cpan.org/search?query=NCM%3a%3aComponent%3a%3aFreeIPA%3a%3aClient&mode=module>`_.

Public methods
==============



- add_service
 
 Add a service with name ``name``.
 


- add_service_host
 
 Add a per-host service ``name`` for host ``host``
 (actual service name will ``<<name``/<host>>>).
 
 Add host ``host`` to list of hosts that can manage this service.
 


- service_has_keytab
 
 Check if a keytab is already made for service with ``name``.
 



