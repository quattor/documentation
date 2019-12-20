
################################
NCM\::Component\::FreeIPA\::Host
################################


****
NAME
****


NCM::Component::FreeIPA::Host adds host related methods to
`NCM::Component::FreeIPA::Client <http://search.cpan.org/search?query=NCM%3a%3aComponent%3a%3aFreeIPA%3a%3aClient&mode=module>`_.

Public methods
==============



- add_host
 
 Add a host. If the host already exists, return undef.
 
 
 - Arguments
  
  
  - fqdn: FQDN hostname
  
  
  
 
 
 - Options (passed to ``Net::FreeIPA::API::api_host_add``).
  
  
  - ip_address: IP to configure DNS entry
  
  
  
  - macaddress: macaddress
  
  
  
 
 


- disable_host
 
 Disable a host with ``fqdn`` hostname.
 


- remove_host
 
 Remove the host ``fqdn``.
 


- host_passwd
 
 Reset and return the one-time password for host ``fqdn``.
 Returns undef if the host already has a keytab or if it doesn't exist.
 



