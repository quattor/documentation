##################################################
NCM\::Component\::network\::types\::network - rule
##################################################

Types
-----

 - **/software/components/network/network_ip_cmd_prefix**
 - **/software/components/network/network_rule**
    - Description: Add rule (IPv4 of IPv6) Presence of ':' in any of the values indicates this is IPv6 related.
    - */software/components/network/network_rule/to*
        - Description: to selector
        - Optional
        - Type: network_ip_cmd_prefix
    - */software/components/network/network_rule/from*
        - Description: from selector
        - Optional
        - Type: network_ip_cmd_prefix
    - */software/components/network/network_rule/not*
        - Description: not action (false value means no not action; also the default when not is not defined)
        - Optional
        - Type: boolean
    - */software/components/network/network_rule/table*
        - Description: routing table action
        - Optional
        - Type: network_valid_routing_table
    - */software/components/network/network_rule/priority*
        - Description: priority, The priority of the rule over the others. Required by Network Manager when setting routing rules.
        - Optional
        - Type: long
        - Range: 0..4294967295
    - */software/components/network/network_rule/command*
        - Description: rule add options to use (cannot be combined with other options)
        - Optional
        - Type: string
