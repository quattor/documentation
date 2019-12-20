###################################
NCM\::Component\::resolver - schema
###################################

Types
-----

 - **/software/components/resolver/component_resolver_type**
    - */software/components/resolver/component_resolver_type/servers*
        - Required
        - Type: type_ip
    - */software/components/resolver/component_resolver_type/search*
        - Optional
        - Type: type_fqdn
    - */software/components/resolver/component_resolver_type/dnscache*
        - Required
        - Type: boolean
        - Default value: false
