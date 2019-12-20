################################
NCM\::Component\::fstab - schema
################################

Types
-----

 - **/software/components/fstab/fstab_protected_entries**
    - Description: Protected mountpoints and filesystem types. mounts is looked for on the second field of fstab, fs_file fs_types is looked for on the third field of fstab, fs_vfstype Default content of mounts is the same content as from the now deprecated protected_mounts field in the structure_component_fstab type
    - */software/components/fstab/fstab_protected_entries/mounts*
        - Required
        - Type: string
    - */software/components/fstab/fstab_protected_entries/fs_types*
        - Optional
        - Type: string
 - **/software/components/fstab/structure_component_fstab**
    - Description: fstab component structure keep entries are always kept, but can be changed static entries can not be changed, but can be deleted protected_mounts is still here for backwards compability, and is the same as keep/mounts
    - */software/components/fstab/structure_component_fstab/keep*
        - Required
        - Type: fstab_protected_entries
    - */software/components/fstab/structure_component_fstab/static*
        - Optional
        - Type: fstab_protected_entries
    - */software/components/fstab/structure_component_fstab/protected_mounts*
        - Optional
        - Type: string
