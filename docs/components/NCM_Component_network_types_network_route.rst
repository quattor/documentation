###################################################
NCM\::Component\::network\::types\::network - route
###################################################

Types
-----

 - **/software/components/network/network_valid_routing_table**
 - **/software/components/network/network_route**
    - Description: Add route (IPv4 of IPv6) Presence of ':' in any of the values indicates this is IPv6 related.
    - */software/components/network/network_route/address*
        - Description: The ADDRESS in ADDRESS/PREFIX via GATEWAY
        - Optional
        - Type: string
    - */software/components/network/network_route/prefix*
        - Description: The PREFIX in ADDRESS/PREFIX via GATEWAY
        - Optional
        - Type: long
    - */software/components/network/network_route/gateway*
        - Description: The GATEWAY in ADDRESS/PREFIX via GATEWAY
        - Optional
        - Type: type_ip
    - */software/components/network/network_route/netmask*
        - Description: alternative notation for prefix (cannot be combined with prefix)
        - Optional
        - Type: type_ip
    - */software/components/network/network_route/table*
        - Description: routing table
        - Optional
        - Type: network_valid_routing_table
    - */software/components/network/network_route/onlink*
        - Description: pretend that the nexthop is directly attached to this link
        - Optional
        - Type: boolean
    - */software/components/network/network_route/command*
        - Description: route add command options to use (cannot be combined with other options)
        - Optional
        - Type: string

Functions
---------

 - network_valid_prefix
