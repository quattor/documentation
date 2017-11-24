
### Types

 - `/software/ceph/ceph_osd_config`
    - Description:  configuration options for a ceph osd daemon 
    - `/software/ceph/ceph_osd_config/osd_deep_scrub_interval`
        - Optional
        - Type: double
    - `/software/ceph/ceph_osd_config/osd_journal_size`
        - Optional
        - Type: long
        - Range: 0..
    - `/software/ceph/ceph_osd_config/osd_max_scrubs`
        - Optional
        - Type: long
        - Range: 0..
    - `/software/ceph/ceph_osd_config/osd_objectstore`
        - Optional
        - Type: string
    - `/software/ceph/ceph_osd_config/osd_op_threads`
        - Optional
        - Type: long
        - Range: 0..
    - `/software/ceph/ceph_osd_config/osd_scrub_begin_hour`
        - Optional
        - Type: long
        - Range: 0..24
    - `/software/ceph/ceph_osd_config/osd_scrub_end_hour`
        - Optional
        - Type: long
        - Range: 0..24
    - `/software/ceph/ceph_osd_config/osd_scrub_load_threshold`
        - Optional
        - Type: double
    - `/software/ceph/ceph_osd_config/osd_scrub_min_interval`
        - Optional
        - Type: double
    - `/software/ceph/ceph_osd_config/osd_scrub_max_interval`
        - Optional
        - Type: double
 - `/software/ceph/ceph_osd`
    - Description: 
ceph osd-specific type
The key of the ceph_osd should be the path to the mounted disk.
This can be an absolute path or a relative one to /var/lib/ceph/osd/
journal_path should be the path to a journal file
This can be an absolute path or a relative one to /var/lib/ceph/log/
With labels osds can be grouped. This should also be defined in root.

    - `/software/ceph/ceph_osd/config`
        - Optional
        - Type: ceph_osd_config
    - `/software/ceph/ceph_osd/in`
        - Optional
        - Type: boolean
    - `/software/ceph/ceph_osd/journal_path`
        - Optional
        - Type: string
    - `/software/ceph/ceph_osd/crush_weight`
        - Optional
        - Type: double
    - `/software/ceph/ceph_osd/labels`
        - Optional
        - Type: string
 - `/software/ceph/ceph_osd_host`
    - Description:  ceph osdhost-specific type, defining all osds on a host 
    - `/software/ceph/ceph_osd_host/fqdn`
        - Optional
        - Type: type_fqdn
    - `/software/ceph/ceph_osd_host/osds`
        - Optional
        - Type: ceph_osd
