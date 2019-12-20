########################################
NCM\::Component\::ceph\::v1 - schema-mds
########################################

Types
-----

 - **/software/components/ceph/ceph_mds_config**
    - Description: configuration options for a ceph mds daemon
    - */software/components/ceph/ceph_mds_config/mds_cache_size*
        - Optional
        - Type: long
        - Default value: 100000
    - */software/components/ceph/ceph_mds_config/mds_max_purge_files*
        - Optional
        - Type: long
        - Default value: 64
    - */software/components/ceph/ceph_mds_config/mds_max_purge_ops*
        - Optional
        - Type: long
        - Default value: 8192
    - */software/components/ceph/ceph_mds_config/mds_max_purge_ops_per_pg*
        - Optional
        - Type: double
        - Default value: 0.5
    - */software/components/ceph/ceph_mds_config/mds_log_max_expiring*
        - Optional
        - Type: long
        - Default value: 20
    - */software/components/ceph/ceph_mds_config/mds_log_max_segments*
        - Optional
        - Type: long
        - Default value: 30
 - **/software/components/ceph/ceph_mds**
    - Description: ceph mds-specific type
    - */software/components/ceph/ceph_mds/fqdn*
        - Required
        - Type: type_fqdn
    - */software/components/ceph/ceph_mds/config*
        - Optional
        - Type: ceph_mds_config
