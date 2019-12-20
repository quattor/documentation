###############################################
NCM\::Component\::openstack\::identity - gather
###############################################

Functions
---------

 - openstack_vivify
    - Description: Given dict as first argument, get nested data (or add structure of dicts), one level per argument The first argument is updated in place if needed.
 - openstack_merge
    - Description: set dict key/value pairs from dict value (3rd arg) to dict data (1st arg) with key (2nd arg) an error is raised when already existing key does not have expected value; 4th arg msg is part of the error message
 - openstack_identity_gather_find_authtoken
    - Description: recursive find for (assumed unique) dict named keystone_authtoken. Returns undef if nothing is found.
 - openstack_identity_gather_service_add
    - Description: update the OS identity data (1st arg) for a service name (2nd arg) with service and endpoint data. 3rd arg is a service data, 4th arg is the endpoint default and 5th argument is host identifier
 - openstack_identity_gather_service
    - Description: update the OS identity data (1st arg) for a single service/flavour dict (2nd arg) 3rd arg is a openstack service, 4th arg is the flavour and 5th argument is host identifier
 - openstack_identity_gather
    - Description: update and return data (1st arg) with the identity data from the openstack configuration of the current host. Data to update is typically the value of the identity client configuration, so users, services, ... etc can be added. If more than one argument is passed, it is treated as external profiles whose openstack configuratiom will also be used to update that identity data. (If short hostname(s) are passed, and the variable OPENSTACK_IDENTITY_GATHER_DOMAIN exists, its value will be suffixed as a domain (no leading '.' required)). If no openstack configuration is found, host is skipped. (If value is a list, it will be treated as a list of hosts.)
