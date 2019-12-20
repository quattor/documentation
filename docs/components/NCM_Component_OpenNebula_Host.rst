
###################################
NCM\::Component\::OpenNebula\::Host
###################################


****
NAME
****


``NCM::Component::OpenNebula::Host`` adds ``KVM`` hosts support to
``NCM::Component::OpenNebula``.

Public methods
==============



- manage_hosts
 
 Adds or removes ``Xen`` or ``KVM`` hosts.
 


- disable_host
 
 Disables failing OpenNebula ``host``.
 This method is called when the ``host`` is not reachable from the ``OpenNebula`` server.
 Always displays a warning message.
 In that case the ``host`` is disabled in the scheduler.
 


- sync_opennebula_hosts
 
 Synchronise hosts ``VMM`` scripts.
 


- enable_node
 
 Execute ssh commands required by OpenNebula
 also it configures ``Ceph`` client if necessary.
 



