#################################
NCM\::Component\::lcmaps - schema
#################################

Types
-----

 - **/software/components/lcmaps/lcmaps_modulespec_type**
    - */software/components/lcmaps/lcmaps_modulespec_type/path*
        - Required
        - Type: string
    - */software/components/lcmaps/lcmaps_modulespec_type/args*
        - Optional
        - Type: string
 - **/software/components/lcmaps/lcmaps_policy_type**
    - */software/components/lcmaps/lcmaps_policy_type/name*
        - Required
        - Type: string
    - */software/components/lcmaps/lcmaps_policy_type/ruleset*
        - Required
        - Type: string
 - **/software/components/lcmaps/lcmaps_file_type**
    - */software/components/lcmaps/lcmaps_file_type/dbpath*
        - Required
        - Type: string
    - */software/components/lcmaps/lcmaps_file_type/modulepath*
        - Required
        - Type: string
    - */software/components/lcmaps/lcmaps_file_type/module*
        - Optional
        - Type: lcmaps_modulespec_type
    - */software/components/lcmaps/lcmaps_file_type/policies*
        - Optional
        - Type: lcmaps_policy_type
 - **/software/components/lcmaps/lcmaps_component**
    - */software/components/lcmaps/lcmaps_component/flavor*
        - Optional
        - Type: string
    - */software/components/lcmaps/lcmaps_component/dbpath*
        - Optional
        - Type: string
    - */software/components/lcmaps/lcmaps_component/modulepath*
        - Optional
        - Type: string
    - */software/components/lcmaps/lcmaps_component/multifile*
        - Optional
        - Type: boolean
    - */software/components/lcmaps/lcmaps_component/module*
        - Optional
        - Type: lcmaps_modulespec_type
    - */software/components/lcmaps/lcmaps_component/policies*
        - Optional
        - Type: lcmaps_policy_type
    - */software/components/lcmaps/lcmaps_component/config*
        - Optional
        - Type: lcmaps_file_type
    - */software/components/lcmaps/lcmaps_component/multifile*
        - Optional
        - Type: boolean

Functions
---------

 - component_lcmaps_valid
