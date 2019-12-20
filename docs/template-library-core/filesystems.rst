###########
filesystems
###########

Types
-----

 - **structure_filesystem**
    - Description: Filestystem definition
    - *structure_filesystem/block_device*
        - Required
        - Type: string
    - *structure_filesystem/format*
        - Required
        - Type: boolean
    - *structure_filesystem/preserve*
        - Required
        - Type: boolean
    - *structure_filesystem/mountpoint*
        - Required
        - Type: string
    - *structure_filesystem/mount*
        - Required
        - Type: boolean
    - *structure_filesystem/mountopts*
        - Required
        - Type: string
        - Default value: defaults
    - *structure_filesystem/type*
        - Required
        - Type: string
    - *structure_filesystem/quota*
        - Optional
        - Type: long
    - *structure_filesystem/freq*
        - Required
        - Type: long
        - Default value: 0
    - *structure_filesystem/pass*
        - Required
        - Type: long
        - Default value: 0
    - *structure_filesystem/mkfsopts*
        - Optional
        - Type: string
    - *structure_filesystem/tuneopts*
        - Optional
        - Type: string
    - *structure_filesystem/label*
        - Optional
        - Type: string
    - *structure_filesystem/ksfsformat*
        - Optional
        - Type: boolean
    - *structure_filesystem/aii*
        - Description: When defined and false, AII will ignore this filesystem
        - Optional
        - Type: boolean

Functions
---------

 - filesystems_uniq_paths
    - Description: check that no duplicate mountpoints or blockdevices are used
    - Arguments:
        - array of structure_filesystem, from quattor/types/system
