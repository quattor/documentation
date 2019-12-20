########################################
NCM\::Component\::ceph\::v1 - schema-rgw
########################################

Types
-----

 - **/software/components/ceph/type_quoted_string**
 - **/software/components/ceph/ceph_radosgw_config**
    - Description: configuration options for a ceph rados gateway instance
    - */software/components/ceph/ceph_radosgw_config/host*
        - Required
        - Type: string
    - */software/components/ceph/ceph_radosgw_config/keyring*
        - Required
        - Type: string
    - */software/components/ceph/ceph_radosgw_config/rgw_socket_path*
        - Required
        - Type: string
    - */software/components/ceph/ceph_radosgw_config/log_file*
        - Required
        - Type: string
        - Default value: /var/log/radosgw/client.radosgw.gateway.log
    - */software/components/ceph/ceph_radosgw_config/rgw_frontends*
        - Required
        - Type: type_quoted_string
        - Default value: "civetweb port=8000"
    - */software/components/ceph/ceph_radosgw_config/rgw_print_continue*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/ceph/ceph_radosgw_config/rgw_dns_name*
        - Required
        - Type: type_fqdn
    - */software/components/ceph/ceph_radosgw_config/rgw_enable_ops_log*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/ceph/ceph_radosgw_config/rgw_enable_usage_log*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/ceph/ceph_radosgw_config/user*
        - Optional
        - Type: string
 - **/software/components/ceph/ceph_radosgw**
    - Description: ceph rados gateway type http://ceph.com/docs/master/radosgw/
    - */software/components/ceph/ceph_radosgw/config*
        - Optional
        - Type: ceph_radosgw_config
 - **/software/components/ceph/ceph_radosgwh**
    - Description: ceph rados gateway host, defining all gateways on a host
    - */software/components/ceph/ceph_radosgwh/fqdn*
        - Required
        - Type: type_fqdn
    - */software/components/ceph/ceph_radosgwh/gateways*
        - Required
        - Type: ceph_radosgw
