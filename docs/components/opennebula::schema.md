
### Types

 - `/software/opennebula/directory`
 - `/software/opennebula/opennebula_mysql_db`
    - `/software/opennebula/opennebula_mysql_db/server`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_mysql_db/port`
        - Optional
        - Type: type_port
    - `/software/opennebula/opennebula_mysql_db/user`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_mysql_db/passwd`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_mysql_db/db_name`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_db`
    - `/software/opennebula/opennebula_db/backend`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_log`
    - `/software/opennebula/opennebula_log/system`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_log/debug_level`
        - Optional
        - Type: long
        - Range: 0..3
 - `/software/opennebula/opennebula_federation`
    - `/software/opennebula/opennebula_federation/mode`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_federation/zone_id`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_federation/master_oned`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_im`
    - `/software/opennebula/opennebula_im/executable`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_im/arguments`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_im/sunstone_name`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_im_mad_collectd`
 - `/software/opennebula/opennebula_im_mad_kvm`
 - `/software/opennebula/opennebula_im_mad_xen`
 - `/software/opennebula/opennebula_im_mad`
    - `/software/opennebula/opennebula_im_mad/collectd`
        - Optional
        - Type: opennebula_im_mad_collectd
    - `/software/opennebula/opennebula_im_mad/kvm`
        - Optional
        - Type: opennebula_im_mad_kvm
    - `/software/opennebula/opennebula_im_mad/xen`
        - Optional
        - Type: opennebula_im_mad_xen
 - `/software/opennebula/opennebula_vm`
    - `/software/opennebula/opennebula_vm/executable`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vm/arguments`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vm/default`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vm/sunstone_name`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vm/imported_vms_actions`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vm/keep_snapshots`
        - Optional
        - Type: boolean
 - `/software/opennebula/opennebula_vm_mad_kvm`
 - `/software/opennebula/opennebula_vm_mad_xen`
 - `/software/opennebula/opennebula_vm_mad`
    - `/software/opennebula/opennebula_vm_mad/kvm`
        - Optional
        - Type: opennebula_vm_mad_kvm
    - `/software/opennebula/opennebula_vm_mad/xen`
        - Optional
        - Type: opennebula_vm_mad_xen
 - `/software/opennebula/opennebula_tm_mad`
    - `/software/opennebula/opennebula_tm_mad/executable`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_tm_mad/arguments`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_datastore_mad`
    - `/software/opennebula/opennebula_datastore_mad/executable`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_datastore_mad/arguments`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_hm_mad`
    - `/software/opennebula/opennebula_hm_mad/executable`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_auth_mad`
    - `/software/opennebula/opennebula_auth_mad/executable`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_auth_mad/authn`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_tm_mad_conf`
    - `/software/opennebula/opennebula_tm_mad_conf/name`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_tm_mad_conf/ln_target`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_tm_mad_conf/clone_target`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_tm_mad_conf/shared`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_tm_mad_conf/ds_migrate`
        - Optional
        - Type: boolean
 - `/software/opennebula/opennebula_ds_mad_conf`
    - Description: 
The  configuration for each driver is defined in DS_MAD_CONF.
These values are used when creating a new datastore and should not be modified
since they defined the datastore behavior.

    - `/software/opennebula/opennebula_ds_mad_conf/name`
        - Description: name of the transfer driver, listed in the -d option of the DS_MAD section
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ds_mad_conf/required_attrs`
        - Description: comma separated list of required attributes in the DS template
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ds_mad_conf/persistent_only`
        - Description: specifies whether the datastore can only manage persistent images
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_ds_mad_conf/marketplace_actions`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_market_mad_conf`
    - Description: 
The  configuration for each driver is defined in MARKET_MAD_CONF.
These values are used when creating a new marketplace and should not be modified
since they define the marketplace behavior.
A public marketplace can be removed even if it has registered apps.

    - `/software/opennebula/opennebula_market_mad_conf/name`
        - Description: name of the market driver
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_market_mad_conf/required_attrs`
        - Description: comma separated list of required attributes in the Market template
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_market_mad_conf/app_actions`
        - Description: list of actions allowed for a MarketPlaceApp.
        monitor: the apps of the marketplace will be monitored.
        create: the app in the marketplace.
        delete: the app from the marketplace.
    
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_market_mad_conf/public`
        - Description: set to TRUE for external marketplaces
        - Optional
        - Type: boolean
 - `/software/opennebula/opennebula_default_cost`
    - Description: 
The following attributes define the default cost for Virtual Machines that don't have
a CPU, MEMORY or DISK cost.
This is used by the oneshowback calculate method.

    - `/software/opennebula/opennebula_default_cost/cpu_cost`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_default_cost/memory_cost`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_default_cost/disk_cost`
        - Optional
        - Type: long
 - `/software/opennebula/opennebula_vnc_ports`
    - Description: 
VNC_BASE_PORT is deprecated since OpenNebula 5.0
OpenNebula will automatically assign start + vmid,
allowing to generate different ports for VMs so they do not collide.

    - `/software/opennebula/opennebula_vnc_ports/start`
        - Description: VNC port pool for automatic VNC port assignment,
    if possible the port will be set to START + VMID
        - Optional
        - Type: long
        - Range: 5900..65535
    - `/software/opennebula/opennebula_vnc_ports/reserved`
        - Optional
        - Type: long
 - `/software/opennebula/opennebula_vlan_ids`
    - Description: 
LAN ID pool for the automatic VLAN_ID assignment.
This pool is for 802.1Q networks (Open vSwitch and 802.1Q drivers).
The driver will try first to allocate VLAN_IDS[START] + VNET_ID

    - `/software/opennebula/opennebula_vlan_ids/start`
        - Description: first VLAN_ID to use
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_vlan_ids/reserved`
        - Optional
        - Type: long
 - `/software/opennebula/opennebula_vxlan_ids`
    - Description: 
Automatic VXLAN Network ID (VNI) assignment.
This is used or vxlan networks.
NOTE: reserved is not supported by this pool

    - `/software/opennebula/opennebula_vxlan_ids/start`
        - Description: first VNI (Virtual Network ID) to use
        - Optional
        - Type: long
 - `/software/opennebula/opennebula_market_mad`
    - Description: 
Drivers to manage different marketplaces, specialized for the storage backend.

    - `/software/opennebula/opennebula_market_mad/executable`
        - Description: path of the transfer driver executable, can be an absolute path or
    relative to $ONE_LOCATION/lib/mads (or /usr/lib/one/mads/ if OpenNebula was
    installed in /)
    
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_market_mad/arguments`
        - Description: arguments for the driver executable:
        -t number of threads, i.e. number of repo operations at the same time
        -m marketplace mads separated by commas
    
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_ceph_datastore`
    - Description: 
type for ceph datastore specific attributes.
ceph_host, ceph_secret, ceph_user, ceph_user_key and pool_name are mandatory

    - `/software/opennebula/opennebula_ceph_datastore/ceph_host`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ceph_datastore/ceph_secret`
        - Optional
        - Type: type_uuid
    - `/software/opennebula/opennebula_ceph_datastore/ceph_user`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ceph_datastore/ceph_user_key`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ceph_datastore/pool_name`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ceph_datastore/rbd_format`
        - Optional
        - Type: long
        - Range: 1..2
 - `/software/opennebula/opennebula_ar`
    - Description: 
type for vnet ars specific attributes.
type and size are mandatory

    - `/software/opennebula/opennebula_ar/type`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ar/ip`
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_ar/size`
        - Optional
        - Type: long
        - Range: 1..
    - `/software/opennebula/opennebula_ar/mac`
        - Optional
        - Type: type_hwaddr
    - `/software/opennebula/opennebula_ar/global_prefix`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_ar/ula_prefix`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_datastore`
    - Description: 
type for an opennebula datastore. Defaults to a ceph datastore (ds_mad is ceph).
shared DS is also supported

    - `/software/opennebula/opennebula_datastore/bridge_list`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_datastore/datastore_capacity_check`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_datastore/disk_type`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_datastore/ds_mad`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_datastore/tm_mad`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_datastore/type`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_datastore/labels`
        - Description: datastore labels is a list of strings to group the datastores under a given name and filter them
    in the admin and cloud views. It is also possible to include in the list
    sub-labels using a common slash: list("Name", "Name/SubName")
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_vnet`
    - `/software/opennebula/opennebula_vnet/bridge`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vnet/vn_mad`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vnet/gateway`
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_vnet/gateway6`
        - Optional
        - Type: type_network_name
    - `/software/opennebula/opennebula_vnet/dns`
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_vnet/network_mask`
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_vnet/network_address`
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_vnet/guest_mtu`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_vnet/context_force_ipv4`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_vnet/search_domain`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vnet/bridge_ovs`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_vnet/vlan`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_vnet/vlan_id`
        - Optional
        - Type: long
        - Range: 0..4095
    - `/software/opennebula/opennebula_vnet/ar`
        - Optional
        - Type: opennebula_ar
    - `/software/opennebula/opennebula_vnet/labels`
        - Description: vnet labels is a list of strings to group the vnets under a given name and filter them
    in the admin and cloud views. It is also possible to include in the list
    sub-labels using a common slash: list("Name", "Name/SubName")
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_user`
    - Description: 
Set OpenNebula regular users and their primary groups.
By default new users are assigned to the users group.

    - `/software/opennebula/opennebula_user/ssh_public_key`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_user/password`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_user/group`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_user/labels`
        - Description: user labels is a list of strings to group the users under a given name and filter them
    in the admin and cloud views. It is also possible to include in the list
    sub-labels using a common slash: list("Name", "Name/SubName")
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_group`
    - Description: 
Set a group name and an optional decription

    - `/software/opennebula/opennebula_group/description`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_group/labels`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_remoteconf_ceph`
    - `/software/opennebula/opennebula_remoteconf_ceph/pool_name`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_remoteconf_ceph/host`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_remoteconf_ceph/ceph_user`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_remoteconf_ceph/staging_dir`
        - Optional
        - Type: directory
    - `/software/opennebula/opennebula_remoteconf_ceph/rbd_format`
        - Optional
        - Type: long
        - Range: 1..2
    - `/software/opennebula/opennebula_remoteconf_ceph/qemu_img_convert_args`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_oned`
    - Description: 
Type that sets the OpenNebula
oned.conf file

    - `/software/opennebula/opennebula_oned/db`
        - Optional
        - Type: opennebula_db
    - `/software/opennebula/opennebula_oned/default_device_prefix`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/onegate_endpoint`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/manager_timer`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/monitoring_interval`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/monitoring_threads`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/host_per_interval`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/host_monitoring_expiration_time`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/vm_individual_monitoring`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_oned/vm_per_interval`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/vm_monitoring_expiration_time`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/vm_submit_on_hold`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_oned/max_conn`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/max_conn_backlog`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/keepalive_timeout`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/keepalive_max_conn`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/timeout`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/rpc_log`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_oned/message_size`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/log_call_format`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/scripts_remote_dir`
        - Optional
        - Type: directory
    - `/software/opennebula/opennebula_oned/log`
        - Optional
        - Type: opennebula_log
    - `/software/opennebula/opennebula_oned/federation`
        - Optional
        - Type: opennebula_federation
    - `/software/opennebula/opennebula_oned/port`
        - Optional
        - Type: type_port
    - `/software/opennebula/opennebula_oned/vnc_base_port`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/network_size`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/mac_prefix`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/datastore_location`
        - Optional
        - Type: directory
    - `/software/opennebula/opennebula_oned/datastore_base_path`
        - Optional
        - Type: directory
    - `/software/opennebula/opennebula_oned/datastore_capacity_check`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_oned/default_image_type`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/default_cdrom_device_prefix`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/session_expiration_time`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/default_umask`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oned/im_mad`
        - Optional
        - Type: opennebula_im_mad
    - `/software/opennebula/opennebula_oned/vm_mad`
        - Optional
        - Type: opennebula_vm_mad
    - `/software/opennebula/opennebula_oned/tm_mad`
        - Optional
        - Type: opennebula_tm_mad
    - `/software/opennebula/opennebula_oned/datastore_mad`
        - Optional
        - Type: opennebula_datastore_mad
    - `/software/opennebula/opennebula_oned/hm_mad`
        - Optional
        - Type: opennebula_hm_mad
    - `/software/opennebula/opennebula_oned/auth_mad`
        - Optional
        - Type: opennebula_auth_mad
    - `/software/opennebula/opennebula_oned/market_mad`
        - Optional
        - Type: opennebula_market_mad
    - `/software/opennebula/opennebula_oned/default_cost`
        - Optional
        - Type: opennebula_default_cost
    - `/software/opennebula/opennebula_oned/listen_address`
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_oned/vnc_ports`
        - Optional
        - Type: opennebula_vnc_ports
    - `/software/opennebula/opennebula_oned/vlan_ids`
        - Optional
        - Type: opennebula_vlan_ids
    - `/software/opennebula/opennebula_oned/vxlan_ids`
        - Optional
        - Type: opennebula_vxlan_ids
    - `/software/opennebula/opennebula_oned/tm_mad_conf`
        - Optional
        - Type: opennebula_tm_mad_conf
    - `/software/opennebula/opennebula_oned/ds_mad_conf`
        - Optional
        - Type: opennebula_ds_mad_conf
    - `/software/opennebula/opennebula_oned/market_mad_conf`
        - Optional
        - Type: opennebula_market_mad_conf
    - `/software/opennebula/opennebula_oned/vm_restricted_attr`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/image_restricted_attr`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/vnet_restricted_attr`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/inherit_datastore_attr`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/inherit_image_attr`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oned/inherit_vnet_attr`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_instance_types`
    - `/software/opennebula/opennebula_instance_types/name`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_instance_types/cpu`
        - Optional
        - Type: long
        - Range: 1..
    - `/software/opennebula/opennebula_instance_types/vcpu`
        - Optional
        - Type: long
        - Range: 1..
    - `/software/opennebula/opennebula_instance_types/memory`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_instance_types/description`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_rpc_service`
    - Description: 
type for opennebula service common RPC attributes.

    - `/software/opennebula/opennebula_rpc_service/one_xmlrpc`
        - Description: OpenNebula daemon RPC contact information
        - Optional
        - Type: type_absoluteURI
    - `/software/opennebula/opennebula_rpc_service/core_auth`
        - Description: authentication driver to communicate with OpenNebula core
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_sunstone`
    - Description: 
Type that sets the OpenNebula
sunstone_server.conf file

    - `/software/opennebula/opennebula_sunstone/env`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/tmpdir`
        - Optional
        - Type: directory
    - `/software/opennebula/opennebula_sunstone/host`
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_sunstone/port`
        - Optional
        - Type: type_port
    - `/software/opennebula/opennebula_sunstone/sessions`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/memcache_host`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/memcache_port`
        - Optional
        - Type: type_port
    - `/software/opennebula/opennebula_sunstone/memcache_namespace`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/debug_level`
        - Optional
        - Type: long
        - Range: 0..3
    - `/software/opennebula/opennebula_sunstone/auth`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/encode_user_password`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_port`
        - Optional
        - Type: type_port
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_support_wss`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_cert`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_key`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_ipv6`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_sunstone/lang`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/table_order`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/marketplace_username`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/marketplace_password`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_sunstone/marketplace_url`
        - Optional
        - Type: type_absoluteURI
    - `/software/opennebula/opennebula_sunstone/oneflow_server`
        - Optional
        - Type: type_absoluteURI
    - `/software/opennebula/opennebula_sunstone/instance_types`
        - Optional
        - Type: opennebula_instance_types
    - `/software/opennebula/opennebula_sunstone/routes`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_oneflow`
    - Description: 
Type that sets the OpenNebula
oneflow-server.conf file

    - `/software/opennebula/opennebula_oneflow/host`
        - Description: host where OneFlow server will run
        - Optional
        - Type: type_ipv4
    - `/software/opennebula/opennebula_oneflow/port`
        - Description: port where OneFlow server will run
        - Optional
        - Type: type_port
    - `/software/opennebula/opennebula_oneflow/lcm_interval`
        - Description: time in seconds between Life Cycle Manager steps
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oneflow/default_cooldown`
        - Description: default cooldown period after a scale operation, in seconds
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_oneflow/shutdown_action`
        - Description: default shutdown action
    terminate : OpenNebula >= 5.0.0
    shutdown : OpenNebula < 5.0.0
    
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oneflow/action_number`
        - Description: default numner of virtual machines that will receive the given call in each interval
    defined by action_period, when an action is performed on a role
        - Optional
        - Type: long
        - Range: 1..
    - `/software/opennebula/opennebula_oneflow/action_period`
        - Optional
        - Type: long
        - Range: 1..
    - `/software/opennebula/opennebula_oneflow/vm_name_template`
        - Description: default name for the Virtual Machines created by OneFlow.
    You can use any of the following placeholders:
        $SERVICE_ID
        $SERVICE_NAME
        $ROLE_NAME
        $VM_NUMBER
    
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_oneflow/debug_level`
        - Description: log debug level
        0 = ERROR
        1 = WARNING
        2 = INFO
        3 = DEBUG
    
        - Optional
        - Type: long
        - Range: 0..3
 - `/software/opennebula/opennebula_kvmrc`
    - Description: 
Type that sets the OpenNebula
VMM kvmrc conf files

    - `/software/opennebula/opennebula_kvmrc/lang`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_kvmrc/libvirt_uri`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_kvmrc/qemu_protocol`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_kvmrc/libvirt_keytab`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_kvmrc/shutdown_timeout`
        - Optional
        - Type: long
    - `/software/opennebula/opennebula_kvmrc/force_destroy`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_kvmrc/cancel_no_acpi`
        - Optional
        - Type: boolean
    - `/software/opennebula/opennebula_kvmrc/default_attach_cache`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_kvmrc/migrate_options`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_kvmrc/default_attach_discard`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_rpc`
    - Description: 
Type that sets the OpenNebula conf
to contact to ONE RPC server

    - `/software/opennebula/opennebula_rpc/port`
        - Optional
        - Type: type_port
    - `/software/opennebula/opennebula_rpc/host`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_rpc/user`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_rpc/password`
        - Optional
        - Type: string
 - `/software/opennebula/opennebula_untouchables`
    - Description: 
Type that sets the OpenNebula
untouchable resources

    - `/software/opennebula/opennebula_untouchables/datastores`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_untouchables/vnets`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_untouchables/users`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_untouchables/groups`
        - Optional
        - Type: string
    - `/software/opennebula/opennebula_untouchables/hosts`
        - Optional
        - Type: string
 - `/software/opennebula/component_opennebula`
    - Description: 
Type to define ONE basic resources
datastores, vnets, hosts names, etc

    - `/software/opennebula/component_opennebula/datastores`
        - Optional
        - Type: opennebula_datastore
    - `/software/opennebula/component_opennebula/groups`
        - Optional
        - Type: opennebula_group
    - `/software/opennebula/component_opennebula/users`
        - Optional
        - Type: opennebula_user
    - `/software/opennebula/component_opennebula/vnets`
        - Optional
        - Type: opennebula_vnet
    - `/software/opennebula/component_opennebula/hosts`
        - Optional
        - Type: string
    - `/software/opennebula/component_opennebula/rpc`
        - Optional
        - Type: opennebula_rpc
    - `/software/opennebula/component_opennebula/untouchables`
        - Optional
        - Type: opennebula_untouchables
    - `/software/opennebula/component_opennebula/oned`
        - Optional
        - Type: opennebula_oned
    - `/software/opennebula/component_opennebula/sunstone`
        - Optional
        - Type: opennebula_sunstone
    - `/software/opennebula/component_opennebula/oneflow`
        - Optional
        - Type: opennebula_oneflow
    - `/software/opennebula/component_opennebula/kvmrc`
        - Optional
        - Type: opennebula_kvmrc
    - `/software/opennebula/component_opennebula/ssh_multiplex`
        - Description: set ssh host multiplex options
        - Optional
        - Type: boolean
    - `/software/opennebula/component_opennebula/cfg_group`
        - Description: in some cases (such a Sunstone standalone configuration with apache), 
    some OpenNebula configuration files should be accessible by a different group (as apache).
    This variable sets the group name to change these files permissions.
        - Optional
        - Type: string
    - `/software/opennebula/component_opennebula/host_ovs`
        - Description: includes the Open vSwitch network drives in your hosts. (OVS must be installed in each host).
    This option is not longer used by ONE >= 5.x versions.
        - Optional
        - Type: boolean
    - `/software/opennebula/component_opennebula/host_hyp`
        - Description: set OpenNebula hosts type
        - Optional
        - Type: string
    - `/software/opennebula/component_opennebula/tm_system_ds`
        - Description: set system Datastore TM_MAD value.
        shared: The storage area for the system datastore is a shared directory across the hosts.
        vmfs: A specialized version of the shared one to use the vmfs file system.
        ssh: Uses a local storage area from each host for the system datastore.
    
        - Optional
        - Type: string

### Functions

 - is_consistent_database
    - Description: 
check if a specific type of database has the right attributes

 - is_consistent_datastore
    - Description: 
check if a specific type of datastore has the right attributes

