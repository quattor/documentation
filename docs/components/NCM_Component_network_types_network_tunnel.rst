####################################################
NCM\::Component\::network\::types\::network - tunnel
####################################################

Types
-----

 - **/software/components/network/network_interface_plugin_vxlan**
    - Description: interface plugin for vxlan support via initscripts-vxlan
    - */software/components/network/network_interface_plugin_vxlan/vni*
        - Description: VXLAN Network Identifier (or VXLAN Segment ID); derived from devicename vxlan[0-9] if not defined
        - Optional
        - Type: long
        - Range: 0..16777216
    - */software/components/network/network_interface_plugin_vxlan/group*
        - Description: multicast ip to join
        - Optional
        - Type: type_ip
    - */software/components/network/network_interface_plugin_vxlan/remote*
        - Description: destination IP address to use in outgoing packets
        - Optional
        - Type: type_ip
    - */software/components/network/network_interface_plugin_vxlan/local*
        - Description: source IP address to use in outgoing packets
        - Optional
        - Type: type_ip
    - */software/components/network/network_interface_plugin_vxlan/dstport*
        - Description: UDP destination port
        - Optional
        - Type: long
        - Range: 2..65535
    - */software/components/network/network_interface_plugin_vxlan/gbp*
        - Description: Group Policy extension
        - Optional
        - Type: boolean
 - **/software/components/network/network_interface_plugin**
    - Description: interface plugin via custom ifup/down[-pre]-local hooks
    - */software/components/network/network_interface_plugin/vxlan*
        - Description: VXLAN support via initscripts-vxlan
        - Optional
        - Type: network_interface_plugin_vxlan
 - **/software/components/network/network_interface_tunnel**
    - */software/components/network/network_interface_tunnel/my_inner_ipaddr*
        - Description: tunnel IP
        - Optional
        - Type: type_ip
    - */software/components/network/network_interface_tunnel/my_inner_prefix*
        - Description: tunnel IP netmask prefix
        - Optional
        - Type: long
        - Range: 0..32
    - */software/components/network/network_interface_tunnel/my_outer_ipaddr*
        - Description: primary local IP address
        - Optional
        - Type: type_ip
    - */software/components/network/network_interface_tunnel/peer_outer_ipaddr*
        - Description: remote peer primary IP address
        - Optional
        - Type: type_ip
    - */software/components/network/network_interface_tunnel/plugin*
        - Optional
        - Type: network_interface_plugin

Functions
---------

 - network_interface_tunnel_validate
    - Description: validate the network_interface tunnel config. error on error
