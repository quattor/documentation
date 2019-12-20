
##################################
NCM\::Component\::FreeIPA\::Client
##################################


****
NAME
****


NCM::Component::FreeIPA::Client is a perl FreeIPA JSON API client
class for Quattor

Private methods
===============



- _initialize
 
 Handle the actual initializtion of new. Return 1 on success, undef otherwise.
 
 
 - log
  
  An ``CAF::Reporter`` instance that can be used for logging
  (it is converted in a logger appropriate for ``Net::FreeIPA``).
  
 
 
 All other arguments and options are passed to `Net::FreeIPA <http://search.cpan.org/search?query=Net%3a%3aFreeIPA&mode=module>`_
 during initialisation.
 



