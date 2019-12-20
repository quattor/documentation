############################################
NCM\::Component\::metaconfig\::lmod - schema
############################################

Types
-----

 - **/software/components/metaconfig/lmod_prop**
    - Description: generate single displayT entry, all keys or names are considered valid
    - */software/components/metaconfig/lmod_prop/short*
        - Required
        - Type: string
    - */software/components/metaconfig/lmod_prop/long*
        - Required
        - Type: string
    - */software/components/metaconfig/lmod_prop/doc*
        - Required
        - Type: string
    - */software/components/metaconfig/lmod_prop/color*
        - Optional
        - Type: string
    - */software/components/metaconfig/lmod_prop/names*
        - Description: override the key with name joined using ':'
        - Optional
        - Type: string
 - **/software/components/metaconfig/lmod_scdescript**
    - */software/components/metaconfig/lmod_scdescript/timestamp*
        - Required
        - Type: string
    - */software/components/metaconfig/lmod_scdescript/dir*
        - Required
        - Type: string
 - **/software/components/metaconfig/lmod_service**
    - */software/components/metaconfig/lmod_service/prop*
        - Required
        - Type: lmod_prop
    - */software/components/metaconfig/lmod_service/scDescript*
        - Optional
        - Type: lmod_scdescript
