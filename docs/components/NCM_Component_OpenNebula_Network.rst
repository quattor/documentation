
######################################
NCM\::Component\::OpenNebula\::Network
######################################


****
NAME
****


``NCM::Component::OpenNebula::Network`` adds ``OpenNebula`` ``VirtualNetwork``
configuration support to `NCM::Component::opennebula <http://search.cpan.org/search?query=NCM%3a%3aComponent%3a%3aopennebula&mode=module>`_.

Public methods
==============



- update_vn_ar
 
 Updates ``VirtualNetwork`` ``ARs``.
 


- get_vnetars
 
 Gets the network ``ARs`` (address range) from ``TT`` file
 and gathers ``VNet`` names and IP/MAC addresses.
 


- remove_and_create_vn_ars
 
 Removes/creates ``ARs`` (address range).
 


- detect_duplicate_ars
 
 Detects duplicate ``VirtualNetwork`` ``ARs`` with
 same IPs or MACs.
 Removes duplicated ``ARs`` (if ``QUATTOR`` flag is set to true).
 


- create_vn_ars
 
 Creates ``VirtualNetwork`` ``AR`` leases.
 


- remove_vn_ars
 
 Removes <VirtualNetwork> ``AR`` leases.
 


- remove_vn_ars
 
 Detects ``Quattor`` flag within ``AR`` template.
 



