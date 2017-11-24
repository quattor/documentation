
### Types

 - `/software/fstab/fstab_protected_entries`
    - Description:
Protected mountpoints and filesystem types.
mounts is looked for on the second field of fstab, fs_file
fs_types is looked for on the third field of fstab, fs_vfstype
Default content of mounts is the same content as from the now deprecated
protected_mounts field in the structure_component_fstab type

    - `/software/fstab/fstab_protected_entries/mounts`
        - Optional
        - Type: string
    - `/software/fstab/fstab_protected_entries/fs_types`
        - Optional
        - Type: string
 - `/software/fstab/structure_component_fstab`
    - Description:
fstab component structure
keep entries are always kept, but can be changed
static entries can not be changed, but can be deleted
protected_mounts is still here for backwards compability, and is the same as keep/mounts

    - `/software/fstab/structure_component_fstab/keep`
        - Optional
        - Type: fstab_protected_entries
    - `/software/fstab/structure_component_fstab/static`
        - Optional
        - Type: fstab_protected_entries
    - `/software/fstab/structure_component_fstab/protected_mounts`
        - Optional
        - Type: string
