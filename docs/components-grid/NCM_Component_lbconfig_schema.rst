###################################
NCM\::Component\::lbconfig - schema
###################################

Types
-----

 - **/software/components/lbconfig/structure_index_list**
 - **/software/components/lbconfig/lbconfig_component**
    - */software/components/lbconfig/lbconfig_component/configFile*
        - Required
        - Type: string
        - Default value: edg_wl_query_index.conf
    - */software/components/lbconfig/lbconfig_component/indicies*
        - Required
        - Type: structure_index_list
