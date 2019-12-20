##############################
NCM\::Component\::nss - schema
##############################

Types
-----

 - **/software/components/nss/component_nss_build**
    - */software/components/nss/component_nss_build/script*
        - Required
        - Type: string
    - */software/components/nss/component_nss_build/depends*
        - Optional
        - Type: string
    - */software/components/nss/component_nss_build/active*
        - Optional
        - Type: boolean
 - **/software/components/nss/component_nss_build_dbs**
    - */software/components/nss/component_nss_build_dbs/db*
        - Optional
        - Type: component_nss_build
    - */software/components/nss/component_nss_build_dbs/nis*
        - Optional
        - Type: component_nss_build
    - */software/components/nss/component_nss_build_dbs/compat*
        - Optional
        - Type: component_nss_build
    - */software/components/nss/component_nss_build_dbs/dns*
        - Optional
        - Type: component_nss_build
    - */software/components/nss/component_nss_build_dbs/files*
        - Optional
        - Type: component_nss_build
    - */software/components/nss/component_nss_build_dbs/ldap*
        - Optional
        - Type: component_nss_build
 - **/software/components/nss/component_nss_db**
 - **/software/components/nss/component_nss_type**
    - */software/components/nss/component_nss_type/build*
        - Optional
        - Type: component_nss_build_dbs
    - */software/components/nss/component_nss_type/databases*
        - Required
        - Type: component_nss_db
