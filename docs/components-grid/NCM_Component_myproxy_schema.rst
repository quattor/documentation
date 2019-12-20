##################################
NCM\::Component\::myproxy - schema
##################################

Types
-----

 - **/software/components/myproxy/myproxy_component_policies**
    - */software/components/myproxy/myproxy_component_policies/renewers*
        - Optional
        - Type: string
    - */software/components/myproxy/myproxy_component_policies/retrievers*
        - Optional
        - Type: string
    - */software/components/myproxy/myproxy_component_policies/keyRetrievers*
        - Optional
        - Type: string
    - */software/components/myproxy/myproxy_component_policies/trustedRetrievers*
        - Optional
        - Type: string
 - **/software/components/myproxy/myproxy_component**
    - */software/components/myproxy/myproxy_component/flavor*
        - Required
        - Type: string
        - Default value: edg
    - */software/components/myproxy/myproxy_component/confFile*
        - Optional
        - Type: string
        - Default value: opt/edg/etc/edg-myproxy.conf
    - */software/components/myproxy/myproxy_component/daemonName*
        - Required
        - Type: string
        - Default value: myproxy
    - */software/components/myproxy/myproxy_component/trustedDNs*
        - Optional
        - Type: string
    - */software/components/myproxy/myproxy_component/authorizedDNs*
        - Optional
        - Type: myproxy_component_policies
    - */software/components/myproxy/myproxy_component/defaultDNs*
        - Optional
        - Type: myproxy_component_policies

Functions
---------

 - component_myproxy_options_valid
