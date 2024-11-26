
###########################
NCM\::Component\::hostsfile
###########################


****
NAME
****


NCM::hostsfile - NCM local hosts file configuration component.


********
SYNOPSIS
********


configure local `/etc/hosts` settings and resources as per CDB


- Configure()

 Updates the ``/etc/hosts`` file with the entries specified within the
 configuration. The entries in the configuration are keyed by the primary
 hostname. If an entry describes a hostname which is already in ``/etc/hosts``
 (either as a primary hostname, or as an alias), then that host entry will
 be left alone (if takeover is false), or will be completely replaced by
 the entry specified in the configuration (if takeover is true).

 A comment ``# NCM`` is added to each line so that any deletions will also be
 cleaned up correctly.

 Returns error in case of a failure.




*********
RESOURCES
*********



* ``/system/network/domainname``

 When specifying hosts within the entries dict, if a hostname is not FQDN
 and there are no aliases defined, then an alias will be automatically
 created using an FQDN formed by joining the shortname with
 this domain.



