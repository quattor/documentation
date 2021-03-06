##################################################
NCM\::Component\::metaconfig\::keepalived - schema
##################################################

Types
-----

 - **/software/components/metaconfig/keepalived_service_global**
    - Description: The global_defs section
    - */software/components/metaconfig/keepalived_service_global/router_id*
        - Required
        - Type: string
 - **/software/components/metaconfig/keepalived_service_vrrpscript**
    - Description: The vrrp_script section
    - */software/components/metaconfig/keepalived_service_vrrpscript/name*
        - Required
        - Type: string
    - */software/components/metaconfig/keepalived_service_vrrpscript/script*
        - Required
        - Type: string
    - */software/components/metaconfig/keepalived_service_vrrpscript/interval*
        - Required
        - Type: long
        - Default value: 2
    - */software/components/metaconfig/keepalived_service_vrrpscript/weight*
        - Required
        - Type: long
        - Default value: 2
 - **/software/components/metaconfig/keepalived_service_vip**
    - Description: The virtual_ipaddress section of the vrrp_instance
    - */software/components/metaconfig/keepalived_service_vip/ipaddress*
        - Required
        - Type: string
    - */software/components/metaconfig/keepalived_service_vip/interface*
        - Required
        - Type: string
    - */software/components/metaconfig/keepalived_service_vip/broadcast*
        - Optional
        - Type: type_ip
 - **/software/components/metaconfig/keepalived_service_vrrpinstance_config**
    - Description: The vrrp_instance configuration
    - */software/components/metaconfig/keepalived_service_vrrpinstance_config/virtual_router_id*
        - Required
        - Type: long
    - */software/components/metaconfig/keepalived_service_vrrpinstance_config/advert_int*
        - Required
        - Type: long
        - Default value: 1
    - */software/components/metaconfig/keepalived_service_vrrpinstance_config/priority*
        - Required
        - Type: long
        - Default value: 100
    - */software/components/metaconfig/keepalived_service_vrrpinstance_config/state*
        - Required
        - Type: choice
    - */software/components/metaconfig/keepalived_service_vrrpinstance_config/interface*
        - Required
        - Type: string
 - **/software/components/metaconfig/keepalived_service_vrrpinstance**
    - Description: The vrrp_instance section
    - */software/components/metaconfig/keepalived_service_vrrpinstance/name*
        - Required
        - Type: string
    - */software/components/metaconfig/keepalived_service_vrrpinstance/config*
        - Required
        - Type: keepalived_service_vrrpinstance_config
    - */software/components/metaconfig/keepalived_service_vrrpinstance/virtual_ipaddresses*
        - Required
        - Type: keepalived_service_vip
    - */software/components/metaconfig/keepalived_service_vrrpinstance/track_scripts*
        - Optional
        - Type: string
    - */software/components/metaconfig/keepalived_service_vrrpinstance/unicast_peer*
        - Optional
        - Type: type_ip
    - */software/components/metaconfig/keepalived_service_vrrpinstance/unicast_src_ip*
        - Optional
        - Type: type_ip
    - */software/components/metaconfig/keepalived_service_vrrpinstance/virtual_routes*
        - Optional
        - Type: string
    - */software/components/metaconfig/keepalived_service_vrrpinstance/track_interface*
        - Optional
        - Type: string
 - **/software/components/metaconfig/keepalived_notify_script**
    - Description: The keepalived notify type
    - */software/components/metaconfig/keepalived_notify_script/script*
        - Required
        - Type: absolute_file_path
    - */software/components/metaconfig/keepalived_notify_script/args*
        - Optional
        - Type: string_trimmed
 - **/software/components/metaconfig/keepalived_service_vrrpsyncgroup**
    - Description: The vrrp_sync_group section
    - */software/components/metaconfig/keepalived_service_vrrpsyncgroup/group*
        - Required
        - Type: string
    - */software/components/metaconfig/keepalived_service_vrrpsyncgroup/notify_master*
        - Optional
        - Type: keepalived_notify_script
    - */software/components/metaconfig/keepalived_service_vrrpsyncgroup/notify_backup*
        - Optional
        - Type: keepalived_notify_script
    - */software/components/metaconfig/keepalived_service_vrrpsyncgroup/notify_fault*
        - Optional
        - Type: keepalived_notify_script
 - **/software/components/metaconfig/keepalived_service**
    - Description: Keepalived config See: http://keepalived.org/
    - */software/components/metaconfig/keepalived_service/global_defs*
        - Optional
        - Type: keepalived_service_global
    - */software/components/metaconfig/keepalived_service/vrrp_scripts*
        - Optional
        - Type: keepalived_service_vrrpscript
    - */software/components/metaconfig/keepalived_service/vrrp_instances*
        - Required
        - Type: keepalived_service_vrrpinstance
    - */software/components/metaconfig/keepalived_service/vrrp_sync_groups*
        - Optional
        - Type: keepalived_service_vrrpsyncgroup
