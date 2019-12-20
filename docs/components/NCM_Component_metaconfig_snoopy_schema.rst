##############################################
NCM\::Component\::metaconfig\::snoopy - schema
##############################################

Types
-----

 - **/software/components/metaconfig/snoopy_filter_chain**
    - */software/components/metaconfig/snoopy_filter_chain/filter*
        - Required
        - Type: string
    - */software/components/metaconfig/snoopy_filter_chain/arguments*
        - Optional
        - Type: string
 - **/software/components/metaconfig/snoopy_output**
 - **/software/components/metaconfig/service_snoopy**
    - */software/components/metaconfig/service_snoopy/filter_chain*
        - Optional
        - Type: snoopy_filter_chain
    - */software/components/metaconfig/service_snoopy/message_format*
        - Optional
        - Type: string
    - */software/components/metaconfig/service_snoopy/output*
        - Optional
        - Type: snoopy_output
    - */software/components/metaconfig/service_snoopy/error_logging*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/service_snoopy/syslog_facility*
        - Optional
        - Type: string
    - */software/components/metaconfig/service_snoopy/syslog_ident*
        - Optional
        - Type: string
    - */software/components/metaconfig/service_snoopy/syslog_level*
        - Optional
        - Type: string
