#################################
NCM\::Component\::gsissh - schema
#################################

Types
-----

 - **/software/components/gsissh/structure_gsissh_server**
    - */software/components/gsissh/structure_gsissh_server/port*
        - Required
        - Type: type_port
    - */software/components/gsissh/structure_gsissh_server/options*
        - Optional
        - Type: string
 - **/software/components/gsissh/structure_gsissh_client**
    - */software/components/gsissh/structure_gsissh_client/options*
        - Optional
        - Type: string
 - **/software/components/gsissh/gsissh_component**
    - */software/components/gsissh/gsissh_component/globus_location*
        - Optional
        - Type: string
    - */software/components/gsissh/gsissh_component/gpt_location*
        - Optional
        - Type: string
    - */software/components/gsissh/gsissh_component/server*
        - Optional
        - Type: structure_gsissh_server
    - */software/components/gsissh/gsissh_component/client*
        - Optional
        - Type: structure_gsissh_client
