############################################
NCM\::Component\::metaconfig\::ceph - schema
############################################

Types
-----

 - **/software/components/metaconfig/ceph_sysconfig**
    - Description: type for configuring the ceph sysconfig file
    - */software/components/metaconfig/ceph_sysconfig/ld_preload*
        - Optional
        - Type: string
    - */software/components/metaconfig/ceph_sysconfig/ceph_auto_restart_on_upgrade*
        - Required
        - Type: boolean
        - Default value: false
