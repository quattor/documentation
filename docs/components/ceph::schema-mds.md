
### Types

 - `/software/ceph/ceph_mds_config`
    - Description:  configuration options for a ceph mds daemon 
    - `/software/ceph/ceph_mds_config/mds_cache_size`
        - Optional
        - Type: long
    - `/software/ceph/ceph_mds_config/mds_max_purge_files`
        - Optional
        - Type: long
    - `/software/ceph/ceph_mds_config/mds_max_purge_ops`
        - Optional
        - Type: long
    - `/software/ceph/ceph_mds_config/mds_max_purge_ops_per_pg`
        - Optional
        - Type: double
 - `/software/ceph/ceph_mds`
    - Description:  ceph mds-specific type 
    - `/software/ceph/ceph_mds/fqdn`
        - Optional
        - Type: type_fqdn
    - `/software/ceph/ceph_mds/config`
        - Optional
        - Type: ceph_mds_config