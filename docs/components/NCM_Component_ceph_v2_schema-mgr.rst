########################################
NCM\::Component\::ceph\::v2 - schema-mgr
########################################

Types
-----

 - **/software/components/ceph/ceph_mgr_module**
    - Description: configuration options for a ceph mgr module like dashboard,prometheus,..
 - **/software/components/ceph/ceph_mgr_config**
    - Description: configuration options for a ceph mgr daemon
    - */software/components/ceph/ceph_mgr_config/modules*
        - Optional
        - Type: ceph_mgr_module
