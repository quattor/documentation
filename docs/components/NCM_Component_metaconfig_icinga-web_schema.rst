##################################################
NCM\::Component\::metaconfig\::icinga-web - schema
##################################################

Types
-----

 - **/software/components/metaconfig/iw_caching_opts**
    - */software/components/metaconfig/iw_caching_opts/enabled*
        - Required
        - Type: boolean
    - */software/components/metaconfig/iw_caching_opts/driver*
        - Required
        - Type: string
        - Default value: apc
    - */software/components/metaconfig/iw_caching_opts/use_query_cache*
        - Required
        - Type: boolean
    - */software/components/metaconfig/iw_caching_opts/use_result_cache*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/iw_caching_opts/result_cache_lifespan*
        - Optional
        - Type: long
        - Range: 0..
        - Default value: 60
 - **/software/components/metaconfig/icinga_database_dsn**
    - */software/components/metaconfig/icinga_database_dsn/protocol*
        - Required
        - Type: string
    - */software/components/metaconfig/icinga_database_dsn/hostname*
        - Required
        - Type: type_hostname
    - */software/components/metaconfig/icinga_database_dsn/username*
        - Required
        - Type: string
    - */software/components/metaconfig/icinga_database_dsn/password*
        - Required
        - Type: string
    - */software/components/metaconfig/icinga_database_dsn/port*
        - Required
        - Type: type_port
    - */software/components/metaconfig/icinga_database_dsn/database_name*
        - Required
        - Type: string
 - **/software/components/metaconfig/manager_attribute**
    - */software/components/metaconfig/manager_attribute/attr_model_loading*
        - Required
        - Type: string
        - Default value: CONSERVATIVE
 - **/software/components/metaconfig/icinga_database**
    - */software/components/metaconfig/icinga_database/dsn*
        - Required
        - Type: icinga_database_dsn
    - */software/components/metaconfig/icinga_database/charset*
        - Required
        - Type: string
        - Default value: utf8
    - */software/components/metaconfig/icinga_database/manager_attributes*
        - Required
        - Type: manager_attribute
    - */software/components/metaconfig/icinga_database/caching*
        - Required
        - Type: iw_caching_opts
    - */software/components/metaconfig/icinga_database/prefix*
        - Optional
        - Type: string
    - */software/components/metaconfig/icinga_database/use_retained*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/icinga_database/load_models*
        - Required
        - Type: string
    - */software/components/metaconfig/icinga_database/models_directory*
        - Required
        - Type: string
    - */software/components/metaconfig/icinga_database/class*
        - Required
        - Type: string
 - **/software/components/metaconfig/icinga_web_service**
    - */software/components/metaconfig/icinga_web_service/icinga_db*
        - Required
        - Type: icinga_database
    - */software/components/metaconfig/icinga_web_service/icinga_web_db*
        - Required
        - Type: icinga_database
