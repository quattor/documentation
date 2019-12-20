##################################
NCM\::Component\::dirperm - schema
##################################

Types
-----

 - **/software/components/dirperm/structure_dirperm_entry**
    - */software/components/dirperm/structure_dirperm_entry/path*
        - Required
        - Type: string
    - */software/components/dirperm/structure_dirperm_entry/perm*
        - Required
        - Type: string
    - */software/components/dirperm/structure_dirperm_entry/owner*
        - Required
        - Type: string
    - */software/components/dirperm/structure_dirperm_entry/type*
        - Required
        - Type: string
    - */software/components/dirperm/structure_dirperm_entry/initdir*
        - Optional
        - Type: string
    - */software/components/dirperm/structure_dirperm_entry/checkmount*
        - Description: ensure that a directory is within a mountpoint configured in the profile
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/dirperm/structure_dirperm_entry/within_mount*
        - Description: ensure that a directory is within a mountpoint
        - Required
        - Type: boolean
        - Default value: false
 - **/software/components/dirperm/component_dirperm**
    - */software/components/dirperm/component_dirperm/paths*
        - Optional
        - Type: structure_dirperm_entry

Functions
---------

 - dirperm_permissions_valid
