##################################
NCM\::Component\::profile - schema
##################################

Types
-----

 - **/software/components/profile/structure_profile_path**
    - */software/components/profile/structure_profile_path/prepend*
        - Optional
        - Type: string
    - */software/components/profile/structure_profile_path/append*
        - Optional
        - Type: string
    - */software/components/profile/structure_profile_path/value*
        - Optional
        - Type: string
 - **/software/components/profile/structure_profile_script**
    - */software/components/profile/structure_profile_script/flavors*
        - Required
        - Type: string
    - */software/components/profile/structure_profile_script/env*
        - Optional
        - Type: string
    - */software/components/profile/structure_profile_script/path*
        - Optional
        - Type: structure_profile_path
    - */software/components/profile/structure_profile_script/flavorSuffix*
        - Required
        - Type: boolean
        - Default value: true
 - **/software/components/profile/component_profile**
    - */software/components/profile/component_profile/configDir*
        - Optional
        - Type: string
    - */software/components/profile/component_profile/configName*
        - Optional
        - Type: string
    - */software/components/profile/component_profile/scripts*
        - Optional
        - Type: structure_profile_script

Functions
---------

 - component_profile_script_valid
