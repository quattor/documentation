###############################################
NCM\::Component\::metaconfig\::zkrsync - schema
###############################################

Types
-----

 - **/software/components/metaconfig/zkrsync_config**
    - Description: type for configuring the zkrsync config file @
    - */software/components/metaconfig/zkrsync_config/servers*
        - Required
        - Type: type_hostport
    - */software/components/metaconfig/zkrsync_config/user*
        - Optional
        - Type: string
    - */software/components/metaconfig/zkrsync_config/passwd*
        - Optional
        - Type: string
    - */software/components/metaconfig/zkrsync_config/destination*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/zkrsync_config/source*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/zkrsync_config/session*
        - Optional
        - Type: string
    - */software/components/metaconfig/zkrsync_config/dryrun*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/rsyncpath*
        - Required
        - Type: string
    - */software/components/metaconfig/zkrsync_config/rsubpaths*
        - Optional
        - Type: string
    - */software/components/metaconfig/zkrsync_config/excludere*
        - Required
        - Type: string
        - Default value: $^
    - */software/components/metaconfig/zkrsync_config/excl_usr*
        - Optional
        - Type: string
        - Default value: root
    - */software/components/metaconfig/zkrsync_config/depth*
        - Optional
        - Type: long
        - Range: 1..
        - Default value: 3
    - */software/components/metaconfig/zkrsync_config/delete*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/checksum*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/hardlinks*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/inplace*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/timeout*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/metaconfig/zkrsync_config/arbitopts*
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/zkrsync_config/verifypath*
        - Optional
        - Type: boolean
        - Default value: true
    - */software/components/metaconfig/zkrsync_config/domain*
        - Optional
        - Type: string
    - */software/components/metaconfig/zkrsync_config/dropcache*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/verbose*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/info*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/daemon*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/zkrsync_config/startport*
        - Optional
        - Type: long
        - Default value: 4444

Functions
---------

 - zkrsync_has_one_role
