
### Types

 - `/software/profile/structure_profile_path`
    - `/software/profile/structure_profile_path/prepend`
        - Optional
        - Type: string
    - `/software/profile/structure_profile_path/append`
        - Optional
        - Type: string
    - `/software/profile/structure_profile_path/value`
        - Optional
        - Type: string
 - `/software/profile/structure_profile_script`
    - `/software/profile/structure_profile_script/flavors`
        - Optional
        - Type: string
    - `/software/profile/structure_profile_script/env`
        - Optional
        - Type: string
    - `/software/profile/structure_profile_script/path`
        - Optional
        - Type: structure_profile_path
    - `/software/profile/structure_profile_script/flavorSuffix`
        - Optional
        - Type: boolean
        - Default value: true
 - `/software/profile/component_profile`
    - `/software/profile/component_profile/configDir`
        - Optional
        - Type: string
    - `/software/profile/component_profile/configName`
        - Optional
        - Type: string
    - `/software/profile/component_profile/scripts`
        - Optional
        - Type: structure_profile_script

### Functions

 - component_profile_script_valid
