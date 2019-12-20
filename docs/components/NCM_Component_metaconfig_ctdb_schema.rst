############################################
NCM\::Component\::metaconfig\::ctdb - schema
############################################

Types
-----

 - **/software/components/metaconfig/ctdb_public_address**
    - Description: type for a ctdb public address @
    - */software/components/metaconfig/ctdb_public_address/network_name*
        - Required
        - Type: type_network_name
    - */software/components/metaconfig/ctdb_public_address/network_interface*
        - Required
        - Type: valid_interface
 - **/software/components/metaconfig/ctdb_public_addresses**
 - **/software/components/metaconfig/ctdb_nodes**
 - **/software/components/metaconfig/ctdb_service**
    - Description: type for configuring the ctdb config file @
    - */software/components/metaconfig/ctdb_service/ctdb_debuglevel*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/metaconfig/ctdb_service/ctdb_logfile*
        - Optional
        - Type: string
    - */software/components/metaconfig/ctdb_service/ctdb_manages_nfs*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/ctdb_service/ctdb_manages_samba*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/ctdb_service/ctdb_nfs_skip_share_check*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/ctdb_service/ctdb_nodes*
        - Optional
        - Type: string
    - */software/components/metaconfig/ctdb_service/ctdb_public_addresses*
        - Optional
        - Type: string
    - */software/components/metaconfig/ctdb_service/ctdb_recovery_lock*
        - Required
        - Type: string
    - */software/components/metaconfig/ctdb_service/ctdb_syslog*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/ctdb_service/nfs_hostname*
        - Optional
        - Type: type_fqdn
    - */software/components/metaconfig/ctdb_service/nfs_server_mode*
        - Optional
        - Type: string
    - */software/components/metaconfig/ctdb_service/prologue*
        - Optional
        - Type: string
