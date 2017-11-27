
### Types

 - `/software/filesystems/structure_component_filesystems`
    - Description: 
when manage_blockdevs is false, filesystems does same as fstab
No other resources here: this component takes its configuration
from fstab component, "/system/filesystems" and "/system/blockdevices"

    - `/software/filesystems/structure_component_filesystems/manage_blockdevs`
        - Optional
        - Type: boolean
        - Default value: true
