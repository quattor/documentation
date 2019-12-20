#################################
NCM\::Component\::afsclt - schema
#################################

Types
-----

 - **/software/components/afsclt/component_afsclt_entry**
    - */software/components/afsclt/component_afsclt_entry/thiscell*
        - Required
        - Type: string
    - */software/components/afsclt/component_afsclt_entry/thesecells*
        - Optional
        - Type: string
    - */software/components/afsclt/component_afsclt_entry/settime*
        - Optional
        - Type: boolean
    - */software/components/afsclt/component_afsclt_entry/cellservdb*
        - Optional
        - Type: string
    - */software/components/afsclt/component_afsclt_entry/afs_mount*
        - Optional
        - Type: string
    - */software/components/afsclt/component_afsclt_entry/cachemount*
        - Optional
        - Type: string
    - */software/components/afsclt/component_afsclt_entry/cachesize*
        - Optional
        - Type: string
    - */software/components/afsclt/component_afsclt_entry/enabled*
        - Required
        - Type: legacy_binary_affirmation_string
    - */software/components/afsclt/component_afsclt_entry/afsd_args*
        - Optional
        - Type: string
