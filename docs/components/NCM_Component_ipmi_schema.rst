###############################
NCM\::Component\::ipmi - schema
###############################

Types
-----

 - **/software/components/ipmi/structure_users**
    - */software/components/ipmi/structure_users/login*
        - Required
        - Type: string
    - */software/components/ipmi/structure_users/password*
        - Required
        - Type: string
    - */software/components/ipmi/structure_users/priv*
        - Optional
        - Type: string
    - */software/components/ipmi/structure_users/userid*
        - Optional
        - Type: long
 - **/software/components/ipmi/component_ipmi_type**
    - */software/components/ipmi/component_ipmi_type/channel*
        - Required
        - Type: long
        - Default value: 1
    - */software/components/ipmi/component_ipmi_type/users*
        - Required
        - Type: structure_users
    - */software/components/ipmi/component_ipmi_type/net_interface*
        - Required
        - Type: string
