################################
NCM\::Component\::named - schema
################################

Types
-----

 - **/software/components/named/component_named**
    - */software/components/named/component_named/serverConfig*
        - Optional
        - Type: string
    - */software/components/named/component_named/configfile*
        - Optional
        - Type: string
    - */software/components/named/component_named/use_localhost*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/named/component_named/start*
        - Optional
        - Type: boolean
    - */software/components/named/component_named/servers*
        - Optional
        - Type: type_ip
    - */software/components/named/component_named/options*
        - Optional
        - Type: string
    - */software/components/named/component_named/search*
        - Optional
        - Type: type_fqdn

Functions
---------

 - component_named_valid
