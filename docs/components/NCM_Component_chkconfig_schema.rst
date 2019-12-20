####################################
NCM\::Component\::chkconfig - schema
####################################

Types
-----

 - **/software/components/chkconfig/service_type**
    - */software/components/chkconfig/service_type/name*
        - Optional
        - Type: string
    - */software/components/chkconfig/service_type/add*
        - Optional
        - Type: boolean
    - */software/components/chkconfig/service_type/del*
        - Optional
        - Type: boolean
    - */software/components/chkconfig/service_type/on*
        - Optional
        - Type: string
    - */software/components/chkconfig/service_type/off*
        - Optional
        - Type: string
    - */software/components/chkconfig/service_type/reset*
        - Optional
        - Type: string
    - */software/components/chkconfig/service_type/startstop*
        - Optional
        - Type: boolean
 - **/software/components/chkconfig/component_chkconfig_type**
    - */software/components/chkconfig/component_chkconfig_type/service*
        - Required
        - Type: service_type
    - */software/components/chkconfig/component_chkconfig_type/default*
        - Optional
        - Type: string

Functions
---------

 - chkconfig_allow_combinations
