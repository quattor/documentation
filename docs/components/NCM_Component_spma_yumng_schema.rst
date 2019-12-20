#######################################
NCM\::Component\::spma\::yumng - schema
#######################################

Types
-----

 - **/software/components/spma/SOFTWARE_GROUP**
    - */software/components/spma/SOFTWARE_GROUP/default*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/spma/SOFTWARE_GROUP/mandatory*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/spma/SOFTWARE_GROUP/optional*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/spma/SOFTWARE_GROUP/names*
        - Required
        - Type: string
 - **/software/components/spma/component_spma_yumng**
    - */software/components/spma/component_spma_yumng/excludes*
        - Optional
        - Type: string
    - */software/components/spma/component_spma_yumng/quattor_os_file*
        - Optional
        - Type: string
    - */software/components/spma/component_spma_yumng/quattor_os_release*
        - Optional
        - Type: string
    - */software/components/spma/component_spma_yumng/run*
        - Optional
        - Type: legacy_binary_affirmation_string
    - */software/components/spma/component_spma_yumng/userpkgs*
        - Optional
        - Type: legacy_binary_affirmation_string
    - */software/components/spma/component_spma_yumng/whitelist*
        - Optional
        - Type: string
    - */software/components/spma/component_spma_yumng/yumconf*
        - Optional
        - Type: string
