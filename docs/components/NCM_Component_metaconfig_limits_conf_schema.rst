###################################################
NCM\::Component\::metaconfig\::limits_conf - schema
###################################################

Types
-----

 - **/software/components/metaconfig/limits_conf_item**
 - **/software/components/metaconfig/limits_conf_entry**
    - */software/components/metaconfig/limits_conf_entry/domain*
        - Required
        - Type: string
    - */software/components/metaconfig/limits_conf_entry/type*
        - Required
        - Type: string
    - */software/components/metaconfig/limits_conf_entry/item*
        - Required
        - Type: limits_conf_item
    - */software/components/metaconfig/limits_conf_entry/value*
        - Required
        - Type: long
        - Range: -1..
 - **/software/components/metaconfig/limits_conf_file**
    - Description: type for configuring the limits.conf file @
    - */software/components/metaconfig/limits_conf_file/entries*
        - Required
        - Type: limits_conf_entry
