
### Types

 - `/software/dirperm/structure_dirperm_entry`
    - `/software/dirperm/structure_dirperm_entry/path`
        - Optional
        - Type: string
    - `/software/dirperm/structure_dirperm_entry/perm`
        - Optional
        - Type: string
    - `/software/dirperm/structure_dirperm_entry/owner`
        - Optional
        - Type: string
    - `/software/dirperm/structure_dirperm_entry/type`
        - Optional
        - Type: string
    - `/software/dirperm/structure_dirperm_entry/initdir`
        - Optional
        - Type: string
    - `/software/dirperm/structure_dirperm_entry/checkmount`
        - Description: ensure that a directory is within a mountpoint configured in the profile
        - Optional
        - Type: boolean
        - Default value: false
    - `/software/dirperm/structure_dirperm_entry/within_mount`
        - Description: ensure that a directory is within a mountpoint
        - Optional
        - Type: boolean
        - Default value: false
 - `/software/dirperm/component_dirperm`
    - `/software/dirperm/component_dirperm/paths`
        - Optional
        - Type: structure_dirperm_entry

### Functions

 - dirperm_permissions_valid
