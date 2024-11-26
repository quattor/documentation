###################################
NCM\::Component\::resolver - schema
###################################

Types
-----

 - **/software/components/resolver/resolver_component_options**
    - Description: See resolv.conf(5). The code supports both boolean options, and those which take an argument (e.g. timeout:n). The component does not introspect these keys, just the type, so new keys can be added to this resource and the component will write them.
    - */software/components/resolver/resolver_component_options/rotate*
        - Optional
        - Type: boolean
    - */software/components/resolver/resolver_component_options/timeout*
        - Optional
        - Type: long
        - Range: 0..30
 - **/software/components/resolver/resolver_component**
    - */software/components/resolver/resolver_component/servers*
        - Required
        - Type: type_ip
    - */software/components/resolver/resolver_component/search*
        - Optional
        - Type: type_fqdn
    - */software/components/resolver/resolver_component/dnscache*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/resolver/resolver_component/options*
        - Optional
        - Type: resolver_component_options
