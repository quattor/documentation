
###################################
NCM\::Component\::interactivelimits
###################################


****
NAME
****


NCM::interactivelimits - NCM interactivelimits configuration component


********
SYNOPSIS
********



- Configure()
 
 Updates the ``/etc/security/limits.conf`` file with system limits
 for interactive users.
 This file is read by ``/lib/security/pam_limits.so`` and the values
 defined there are respected.
 Returns error in case of failure.
 



*********
RESOURCES
*********



* ``/software/components/interactivelimits/active`` : boolean
 
 Activates/deactivates the component.
 


* ``/software/components/interactivelimits/values`` : list
 
 Defines all values that should be configured in ``/etc/security/limits.conf``.
 
 Example of such a definition from a node profile:
 
 
 .. code-block:: perl
 
    "/software/components/interactivelimits/values" = list(
      list("username", "soft", "core", "0"),
      list("username", "hard", "nofile", "65536"),
      list("username", "soft", "nproc", "16384"),
      list("username", "hard", "as", "unlimited"),
    );
 
 


