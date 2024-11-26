#################################################
NCM\::Component\::network\::types\::network - ovs
#################################################

Types
-----

 - **/software/components/network/network_interface_ovs**
    - */software/components/network/network_interface_ovs/ovs_bridge*
        - Optional
        - Type: valid_interface
    - */software/components/network/network_interface_ovs/ovs_extra*
        - Optional
        - Type: string
    - */software/components/network/network_interface_ovs/ovs_opts*
        - Optional
        - Type: string
    - */software/components/network/network_interface_ovs/ovs_patch_peer*
        - Optional
        - Type: string
    - */software/components/network/network_interface_ovs/ovs_tunnel_opts*
        - Optional
        - Type: string
    - */software/components/network/network_interface_ovs/ovs_tunnel_type*
        - Optional
        - Type: choice

Functions
---------

 - network_interface_ovs_validate
    - Description: validate the network_interface ovs config. error on error
