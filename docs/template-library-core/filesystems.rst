###########
filesystems
###########

Types
-----

 - **structure_filesystem**
    - Description: Filestystem definition
    - *structure_filesystem/block_device*
        - Description: filesystem blockdevice - References an entry in /software/components/blockdevices
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
        - Description: Mount options
        - Required
        - Type: string
        - Default value: defaults
    - *structure_filesystem/type*
        - Description: Filesystem type
        - Required
        - Type: choice
    - *structure_filesystem/quota*
        - Description: Quota percentage
        - Optional
        - Type: long
    - *structure_filesystem/freq*
        - Description: Dump frequency
        - Required
        - Type: long
        - Default value: 0
    - *structure_filesystem/pass*
        - Description: fsck pass number
        - Required
        - Type: long
        - Default value: 0
    - *structure_filesystem/mkfsopts*
        - Description: Extra options passed to mkfs
        - Optional
        - Type: string
    - *structure_filesystem/tuneopts*
        - Description: Options for filesystem tuning commands (tune2fs, xfs_admin...)
        - Optional
        - Type: string
    - *structure_filesystem/label*
        - Description: Filesystem label, as in LABEL=foo
        - Optional
        - Type: string
    - *structure_filesystem/ksfsformat*
        - Description: If true, anaconda formats the filesystem (with undef/false, --noformat is used)
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
