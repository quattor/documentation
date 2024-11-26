###############################################################
NCM\::Component\::network\::types\::network\::backend - nmstate
###############################################################

Types
-----

 - **/software/components/network/structure_nm_device_config**
    - Description: NetworkManager device configuration for drop in config file.
    - */software/components/network/structure_nm_device_config/keep-configuration*
        - Optional
        - Type: choice
 - **/software/components/network/structure_network_backend_specific**
    - */software/components/network/structure_network_backend_specific/manage_dns*
        - Description: let NetworkManager manage the dns
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/network/structure_network_backend_specific/clean_inactive_conn*
        - Description: let ncm-network cleanup inactive connections
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/network/structure_network_backend_specific/device_config*
        - Optional
        - Type: structure_nm_device_config
 - **/software/components/network/structure_network_rule_backend_specific**
    - */software/components/network/structure_network_rule_backend_specific/action*
        - Description: action used by nmstate module
        - Optional
        - Type: choice
    - */software/components/network/structure_network_rule_backend_specific/state*
        - Description: state used by nmstate module, Can only set to absent for deleting matching route rules
        - Optional
        - Type: choice
    - */software/components/network/structure_network_rule_backend_specific/iif*
        - Description: iif used by nmstate module, Incoming interface name
        - Optional
        - Type: string
    - */software/components/network/structure_network_rule_backend_specific/fwmark*
        - Description: fwmark used by nmstate module. Select the fwmark value to match
        - Optional
        - Type: string
    - */software/components/network/structure_network_rule_backend_specific/fwmask*
        - Description: fwmask used by nmstate module. Select the fwmask value to match
        - Optional
        - Type: string

Functions
---------

 - network_valid_route
 - network_valid_rule
