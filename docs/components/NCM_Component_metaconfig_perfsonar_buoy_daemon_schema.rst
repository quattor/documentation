#################################################################
NCM\::Component\::metaconfig\::perfsonar\::buoy\::daemon - schema
#################################################################

Types
-----

 - **/software/components/metaconfig/perfsonarbuoy**
    - */software/components/metaconfig/perfsonarbuoy/maintenance_interval*
        - Required
        - Type: long
        - Range: 0..
        - Default value: 10
    - */software/components/metaconfig/perfsonarbuoy/enable_registration*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/metaconfig/perfsonarbuoy/ls_registration_interval*
        - Required
        - Type: long
        - Range: 0..
        - Default value: 60
    - */software/components/metaconfig/perfsonarbuoy/ls_instance*
        - Required
        - Type: type_absoluteURI
        - Default value: http://localhost:9995/perfsonar_PS/services/hLS
    - */software/components/metaconfig/perfsonarbuoy/metadata_db_file*
        - Required
        - Type: string
        - Default value: /var/lib/perfsonar/perfsonarbuoy_ma/store.xml
    - */software/components/metaconfig/perfsonarbuoy/metadata_db_type*
        - Required
        - Type: string
        - Default value: file
    - */software/components/metaconfig/perfsonarbuoy/owmesh*
        - Required
        - Type: string
        - Default value: /opt/perfsonar_ps/perfsonarbuoy_ma/etc
    - */software/components/metaconfig/perfsonarbuoy/service_accesspoint*
        - Required
        - Type: type_absoluteURI
        - Default value: http://localhost:8085/perfsonar_PS/services/pSB
    - */software/components/metaconfig/perfsonarbuoy/service_description*
        - Required
        - Type: string
    - */software/components/metaconfig/perfsonarbuoy/service_name*
        - Required
        - Type: string
        - Default value: perfSONARBUOY MA
    - */software/components/metaconfig/perfsonarbuoy/service_type*
        - Required
        - Type: string
        - Default value: MA
 - **/software/components/metaconfig/perfsonar_ma_endpoint**
    - */software/components/metaconfig/perfsonar_ma_endpoint/module*
        - Required
        - Type: string
        - Default value: perfSONAR_PS::Services::MA::perfSONARBUOY
    - */software/components/metaconfig/perfsonar_ma_endpoint/name*
        - Required
        - Type: string
    - */software/components/metaconfig/perfsonar_ma_endpoint/buoy*
        - Required
        - Type: perfsonarbuoy
 - **/software/components/metaconfig/buoydaemon_port**
    - */software/components/metaconfig/buoydaemon_port/port*
        - Required
        - Type: type_port
        - Default value: 8085
    - */software/components/metaconfig/buoydaemon_port/endpoint*
        - Required
        - Type: perfsonar_ma_endpoint
 - **/software/components/metaconfig/buoydaemon**
    - */software/components/metaconfig/buoydaemon/ports*
        - Required
        - Type: buoydaemon_port
    - */software/components/metaconfig/buoydaemon/reaper_interval*
        - Required
        - Type: long
        - Range: 0..
        - Default value: 20
    - */software/components/metaconfig/buoydaemon/root_hints_file*
        - Optional
        - Type: string
    - */software/components/metaconfig/buoydaemon/root_hints_url*
        - Optional
        - Type: type_absoluteURI
    - */software/components/metaconfig/buoydaemon/disable_echo*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/buoydaemon/ls_instance*
        - Required
        - Type: type_absoluteURI
        - Default value: http://localhost:9995/perfsonar_PS/services/hLS
    - */software/components/metaconfig/buoydaemon/ls_registration_interval*
        - Required
        - Type: long
        - Range: 0..
        - Default value: 60
    - */software/components/metaconfig/buoydaemon/max_worker_lifetime*
        - Required
        - Type: long
        - Range: 0..
        - Default value: 300
    - */software/components/metaconfig/buoydaemon/max_worker_processes*
        - Required
        - Type: long
        - Range: 0..
        - Default value: 30
    - */software/components/metaconfig/buoydaemon/pid_dir*
        - Required
        - Type: string
        - Default value: /var/lib/perfsonar/perfsonarbuoy_ma
    - */software/components/metaconfig/buoydaemon/pid_file*
        - Required
        - Type: string
        - Default value: perfsonarbuoy_ma.pid
