
################################
NCM\::Component\::FreeIPA\::User
################################


****
NAME
****


NCM::Component::FreeIPA::User adds host related methods to
`NCM::Component::FreeIPA::Client <http://search.cpan.org/search?query=NCM%3a%3aComponent%3a%3aFreeIPA%3a%3aClient&mode=module>`_.

Public methods
==============



- add_user
 
 Add a user. If the user already exists, return undef.
 
 
 - Arguments
  
  
  - uid: User uid
  
  
  
 
 
 - Options (passed to ``Net::FreeIPA::API::api_user_add``).
  
  
  - homedirectory
  
  
  
  - gecos
  
  
  
  - loginshell
  
  
  
  - uidnumber
  
  
  
  - gidnumber
  
  
  
  - ipasshpubkey
  
  
  
 
 


- disable_user
 
 Disable a user with ``uid``.
 


- remove_user
 
 Remove the user ``uid``  (preserve=1).
 


- user_passwd
 
 Reset and return a new random password for user ``uid``.
 Returns undef if the user doesn't exist.
 



