###################
functions\::network
###################

Variables
---------

 - MTU
    - Description: dict defining a non default MTU size for each interface in the system. dict keys can be an interface name, an interface type (e.g. eth, em), DEFAULT or BOOT. BOOT entry is applied to main interface (no explicit value must exist for it). DEFAULT entry is applied to all interfaces without an explicit value defined.

Functions
---------

 - set_interface_defaults
    - Arguments:
        - a dict with defaults (mandatory 'netmask' and 'gateway', optional 'broadcast')
 - boot_nic
 - copy_network_params
 - ip_in_network
    - Arguments:
        - ipv4 address to test
        - network address (is always recomputed using subnet mask)
        - subnet mask
 - get_subnet_params
    - Arguments:
        - subnet list, a list of dict where the keys are all the properties supported by structure_interface + 'subnet' which is the subnet number (result of applying the mask to the address. `subnet` key is mandatory, 'netmask` defaults to 255.255.255.0.
        - ip address to test
 - subnet_prefix_to_mask
    - Arguments:
        - prefix
 - subnet_mask_to_prefix
    - Arguments:
        - netmask
