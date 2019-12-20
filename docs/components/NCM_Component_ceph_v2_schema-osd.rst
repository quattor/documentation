########################################
NCM\::Component\::ceph\::v2 - schema-osd
########################################

Types
-----

 - **/software/components/ceph/ceph_osd_config**
    - Description: configuration options for a ceph osd daemon
    - */software/components/ceph/ceph_osd_config/osd_deep_scrub_interval*
        - Optional
        - Type: double
    - */software/components/ceph/ceph_osd_config/osd_journal_size*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/ceph/ceph_osd_config/osd_max_scrubs*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/ceph/ceph_osd_config/osd_objectstore*
        - Optional
        - Type: string
    - */software/components/ceph/ceph_osd_config/osd_op_threads*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/ceph/ceph_osd_config/osd_scrub_begin_hour*
        - Optional
        - Type: long
        - Range: 0..24
    - */software/components/ceph/ceph_osd_config/osd_scrub_end_hour*
        - Optional
        - Type: long
        - Range: 0..24
    - */software/components/ceph/ceph_osd_config/osd_scrub_load_threshold*
        - Optional
        - Type: double
    - */software/components/ceph/ceph_osd_config/osd_scrub_min_interval*
        - Optional
        - Type: double
    - */software/components/ceph/ceph_osd_config/osd_scrub_max_interval*
        - Optional
        - Type: double
 - **/software/components/ceph/ceph_osd**
    - Description: ceph osd-specific type Only bluestore support for now dmcrypt supported with ceph-volume > 12.2.3
    - */software/components/ceph/ceph_osd/class*
        - Optional
        - Type: string
    - */software/components/ceph/ceph_osd/storetype*
        - Required
        - Type: choice
        - Default value: bluestore
    - */software/components/ceph/ceph_osd/dmcrypt*
        - Optional
        - Type: boolean
