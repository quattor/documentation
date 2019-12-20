
#################################
NCM\::Component\::FreeIPA\::Group
#################################


****
NAME
****


NCM::Component::FreeIPA::Group adds group related methods to
`NCM::Component::FreeIPA::Client <http://search.cpan.org/search?query=NCM%3a%3aComponent%3a%3aFreeIPA%3a%3aClient&mode=module>`_.

Public methods
==============



- add_group
 
 Add a group with name ``gid``.
 
 
 - Arguments
  
  
  - gid: group gid
  
  
  
 
 
 - Options (passed to ``Net::FreeIPA::API::api_group_add``).
  
  
  - gidnumber
  
  
  
 
 


- add_group_member
 
 Add the members to group ``gid`` using options
 (options are passed to ``api_group_add_member``).
 



