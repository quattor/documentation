##############################################
NCM\::Component\::metaconfig\::pakiti - schema
##############################################

Types
-----

 - **/software/components/metaconfig/pakiti_client2**
    - */software/components/metaconfig/pakiti_client2/server_name*
        - Required
        - Type: type_hostname
    - */software/components/metaconfig/pakiti_client2/port*
        - Required
        - Type: type_port
        - Default value: 80
    - */software/components/metaconfig/pakiti_client2/url*
        - Required
        - Type: string
        - Default value: /feed/
    - */software/components/metaconfig/pakiti_client2/ca_path*
        - Optional
        - Type: string
    - */software/components/metaconfig/pakiti_client2/tag*
        - Optional
        - Type: string
    - */software/components/metaconfig/pakiti_client2/connection_method*
        - Optional
        - Type: string
