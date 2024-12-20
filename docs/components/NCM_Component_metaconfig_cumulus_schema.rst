###############################################
NCM\::Component\::metaconfig\::cumulus - schema
###############################################

Types
-----

 - **/software/components/metaconfig/cumulus_port**
 - **/software/components/metaconfig/cumulus_ipv4**
 - **/software/components/metaconfig/cumulus_vlan**
 - **/software/components/metaconfig/cumulus_vrf**
 - **/software/components/metaconfig/cumulus_port_speed**
    - Description: in 1000
 - **/software/components/metaconfig/cumulus_interface_bridge**
    - */software/components/metaconfig/cumulus_interface_bridge/access*
        - Description: access port to VLAN
        - Optional
        - Type: cumulus_vlan
    - */software/components/metaconfig/cumulus_interface_bridge/vids*
        - Description: tagged VLANs, VLAN for untagged traffic is bridge or interface pvid
        - Optional
        - Type: cumulus_vlan
    - */software/components/metaconfig/cumulus_interface_bridge/enable*
        - Description: interface is part of bridge (default called bridge)
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/metaconfig/cumulus_interface_bridge/pvid*
        - Description: VLAN for untagged packets (default is bridge pvid)
        - Optional
        - Type: cumulus_vlan
 - **/software/components/metaconfig/cumulus_interface_bridge_common**
    - */software/components/metaconfig/cumulus_interface_bridge_common/alias*
        - Description: comment field
        - Optional
        - Type: string
    - */software/components/metaconfig/cumulus_interface_bridge_common/address*
        - Description: clag ip address
        - Optional
        - Type: cumulus_ipv4
    - */software/components/metaconfig/cumulus_interface_bridge_common/mask*
        - Description: address subnet prefix
        - Optional
        - Type: long
        - Range: 0..32
    - */software/components/metaconfig/cumulus_interface_bridge_common/vrf*
        - Description: VRF (mgmt is reserved for the managment interface only)
        - Optional
        - Type: cumulus_vrf
 - **/software/components/metaconfig/cumulus_interface_common**
    - */software/components/metaconfig/cumulus_interface_common/bridge*
        - Required
        - Type: cumulus_interface_bridge
 - **/software/components/metaconfig/cumulus_clagd_backup**
    - */software/components/metaconfig/cumulus_clagd_backup/ip*
        - Required
        - Type: cumulus_ipv4
    - */software/components/metaconfig/cumulus_clagd_backup/vrf*
        - Optional
        - Type: cumulus_vrf
 - **/software/components/metaconfig/cumulus_clagd**
    - */software/components/metaconfig/cumulus_clagd/peer-ip*
        - Required
        - Type: cumulus_ipv4
    - */software/components/metaconfig/cumulus_clagd/sys-mac*
        - Description: MAC should be the same for both MLAG members
        - Required
        - Type: type_hwaddr
    - */software/components/metaconfig/cumulus_clagd/backup-ip*
        - Required
        - Type: cumulus_clagd_backup
    - */software/components/metaconfig/cumulus_clagd/priority*
        - Optional
        - Type: long
        - Range: 0..65535
 - **/software/components/metaconfig/cumulus_peerlink**
    - */software/components/metaconfig/cumulus_peerlink/slaves*
        - Description: bond slaves for the link
        - Required
        - Type: cumulus_port
    - */software/components/metaconfig/cumulus_peerlink/vlan*
        - Description: vlan dedicated to the peerlink
        - Required
        - Type: cumulus_vlan
        - Default value: 4094
    - */software/components/metaconfig/cumulus_peerlink/clagd*
        - Required
        - Type: cumulus_clagd
 - **/software/components/metaconfig/cumulus_interface_link**
    - */software/components/metaconfig/cumulus_interface_link/autoneg*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_interface_link/speed*
        - Description: in 1000
        - Optional
        - Type: cumulus_port_speed
 - **/software/components/metaconfig/cumulus_interface**
    - */software/components/metaconfig/cumulus_interface/inet*
        - Optional
        - Type: choice
    - */software/components/metaconfig/cumulus_interface/gateway*
        - Optional
        - Type: type_ipv4
    - */software/components/metaconfig/cumulus_interface/slaves*
        - Description: bond slaves for the link
        - Optional
        - Type: cumulus_port
    - */software/components/metaconfig/cumulus_interface/post-up*
        - Description: command to run after interface is up
        - Optional
        - Type: string
    - */software/components/metaconfig/cumulus_interface/clag-id*
        - Description: mandatory and unique for dual-connected hosts, using ports on different MLAG members
        - Optional
        - Type: long
        - Range: 0..65535
    - */software/components/metaconfig/cumulus_interface/link*
        - Optional
        - Type: cumulus_interface_link
    - */software/components/metaconfig/cumulus_interface/bond-lacp-bypass-allow*
        - Description: LACP bypass (eg to PXE hosts with LACP)
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_interface/mstpctl-bpduguard*
        - Description: STP BPDU Guard
        - Optional
        - Type: boolean
 - **/software/components/metaconfig/cumulus_bridge_common**
    - */software/components/metaconfig/cumulus_bridge_common/stp*
        - Description: STP
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_bridge_common/vlan-aware*
        - Description: VLAN aware
        - Optional
        - Type: boolean
 - **/software/components/metaconfig/cumulus_bridge**
    - */software/components/metaconfig/cumulus_bridge/pvid*
        - Description: VLAN for untagged packets
        - Optional
        - Type: cumulus_vlan
    - */software/components/metaconfig/cumulus_bridge/vids*
        - Description: Supported VLANs
        - Optional
        - Type: cumulus_vlan
    - */software/components/metaconfig/cumulus_bridge/mcsnoop*
        - Description: enable/disable multicast snooping
        - Optional
        - Type: boolean
 - **/software/components/metaconfig/cumulus_bridge_traditional**
    - */software/components/metaconfig/cumulus_bridge_traditional/ports*
        - Description: interfaces that are part of this bridge
        - Required
        - Type: string
    - */software/components/metaconfig/cumulus_bridge_traditional/vid*
        - Description: VLAN id, when defined, will be added to interfaces that do not have a vlan tag
        - Optional
        - Type: cumulus_vlan
 - **/software/components/metaconfig/cumulus_interfaces**
    - */software/components/metaconfig/cumulus_interfaces/interfaces*
        - Description: interfaces
        - Optional
        - Type: cumulus_interface
    - */software/components/metaconfig/cumulus_interfaces/peerlink*
        - Description: MLAG peerlink configuration
        - Optional
        - Type: cumulus_peerlink
    - */software/components/metaconfig/cumulus_interfaces/bridge*
        - Description: single bridge, reserved name for vlan-aware bridge. use 'bridges' for traditional bridges
        - Optional
        - Type: cumulus_bridge
    - */software/components/metaconfig/cumulus_interfaces/bridges*
        - Description: traditional bridge(s). key makes interface "br-<key>"
        - Optional
        - Type: cumulus_bridge_traditional
 - **/software/components/metaconfig/cumulus_ports_port**
    - Description: a port in a switch. default setting is a disabled port.
    - */software/components/metaconfig/cumulus_ports_port/speed*
        - Required
        - Type: cumulus_port_speed
        - Default value: 1
    - */software/components/metaconfig/cumulus_ports_port/number*
        - Description: number of ports. 0 is disabled port, -1 is short for number:1,speed:default
        - Required
        - Type: long
        - Range: -1..
 - **/software/components/metaconfig/cumulus_ports**
    - */software/components/metaconfig/cumulus_ports/ports*
        - Description: port numbers are increased with 1 relative to the index in the list
        - Required
        - Type: cumulus_ports_port
    - */software/components/metaconfig/cumulus_ports/default*
        - Description: default port speed
        - Required
        - Type: cumulus_port_speed
 - **/software/components/metaconfig/cumulus_frr_route**
    - */software/components/metaconfig/cumulus_frr_route/network*
        - Description: network
        - Required
        - Type: type_ipv4
    - */software/components/metaconfig/cumulus_frr_route/mask*
        - Description: network mask
        - Required
        - Type: long
        - Range: 0..32
    - */software/components/metaconfig/cumulus_frr_route/nexthop*
        - Description: nethop ip or blackhole null0
        - Required
        - Type: string
 - **/software/components/metaconfig/cumulus_bgp_router**
    - */software/components/metaconfig/cumulus_bgp_router/asn*
        - Description: AS number
        - Required
        - Type: long
        - Range: 1..65535
    - */software/components/metaconfig/cumulus_bgp_router/routerid*
        - Description: router ID
        - Required
        - Type: type_ipv4
    - */software/components/metaconfig/cumulus_bgp_router/external*
        - Description: external neighbor
        - Required
        - Type: type_ipv4
    - */software/components/metaconfig/cumulus_bgp_router/ipv4*
        - Description: ipv4 networks
        - Required
        - Type: type_ipv4_netmask_pair
 - **/software/components/metaconfig/cumulus_frr**
    - Description: Simple/minimal FRRouting config file, useful for static routing in VRF setup
    - */software/components/metaconfig/cumulus_frr/vrf*
        - Description: Routes per VRF (key is VRF name)
        - Optional
        - Type: cumulus_frr_route
    - */software/components/metaconfig/cumulus_frr/bgp*
        - Description: List of bgp routers per VRF (VRF is the key)
        - Optional
        - Type: cumulus_bgp_router
 - **/software/components/metaconfig/cumulus_acl_rule_tcp_flag**
 - **/software/components/metaconfig/cumulus_acl_rule_tcp_flags**
    - */software/components/metaconfig/cumulus_acl_rule_tcp_flags/mask*
        - Required
        - Type: cumulus_acl_rule_tcp_flag
    - */software/components/metaconfig/cumulus_acl_rule_tcp_flags/compare*
        - Required
        - Type: cumulus_acl_rule_tcp_flag
 - **/software/components/metaconfig/cumulus_acl_rule_invert**
    - Description: invert options
    - */software/components/metaconfig/cumulus_acl_rule_invert/protocol*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_acl_rule_invert/source*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_acl_rule_invert/sport*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_acl_rule_invert/destination*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_acl_rule_invert/dport*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_acl_rule_invert/tcp-flags*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_acl_rule_invert/in-interface*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cumulus_acl_rule_invert/out-interface*
        - Optional
        - Type: boolean
 - **/software/components/metaconfig/cumulus_acl_rule**
    - Description: iptable based, using long option names. Only default filter table is supported atm.
    - */software/components/metaconfig/cumulus_acl_rule/append*
        - Description: Supported chains form default filter table; the rule is appended
        - Required
        - Type: choice
    - */software/components/metaconfig/cumulus_acl_rule/jump*
        - Description: No user defined chains supported, only ACCEPT and DROP
        - Required
        - Type: choice
    - */software/components/metaconfig/cumulus_acl_rule/protocol*
        - Description: protocol
        - Optional
        - Type: choice
    - */software/components/metaconfig/cumulus_acl_rule/source*
        - Description: source
        - Optional
        - Type: type_ipv4_netmask_pair
    - */software/components/metaconfig/cumulus_acl_rule/sport*
        - Description: port or port range
        - Optional
        - Type: type_port
    - */software/components/metaconfig/cumulus_acl_rule/destination*
        - Description: destination
        - Optional
        - Type: type_ipv4_netmask_pair
    - */software/components/metaconfig/cumulus_acl_rule/dport*
        - Description: port or port range
        - Optional
        - Type: type_port
    - */software/components/metaconfig/cumulus_acl_rule/in-interface*
        - Optional
        - Type: string
    - */software/components/metaconfig/cumulus_acl_rule/out-interface*
        - Optional
        - Type: string
    - */software/components/metaconfig/cumulus_acl_rule/tcp-flags*
        - Optional
        - Type: cumulus_acl_rule_tcp_flags
    - */software/components/metaconfig/cumulus_acl_rule/invert*
        - Optional
        - Type: cumulus_acl_rule_invert
 - **/software/components/metaconfig/cumulus_acl**
    - Description: Simple/minimal support for ACL policy. Each key is a section
    - */software/components/metaconfig/cumulus_acl/iptables*
        - Optional
        - Type: cumulus_acl_rule
 - **/software/components/metaconfig/cumulus_initialise**
    - Description: Some metadata for the initialisation script
    - */software/components/metaconfig/cumulus_initialise/domainname*
        - Required
        - Type: type_fqdn
    - */software/components/metaconfig/cumulus_initialise/hostname*
        - Required
        - Type: type_shorthostname
    - */software/components/metaconfig/cumulus_initialise/ip*
        - Required
        - Type: type_ipv4
    - */software/components/metaconfig/cumulus_initialise/timezone*
        - Required
        - Type: string
    - */software/components/metaconfig/cumulus_initialise/root_keys*
        - Optional
        - Type: string
    - */software/components/metaconfig/cumulus_initialise/cumulus_keys*
        - Optional
        - Type: string
