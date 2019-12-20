###############################################
NCM\::Component\::metaconfig\::mlocate - schema
###############################################

Types
-----

 - **/software/components/metaconfig/prunename**
    - Description: Prunename can not contain slashes.
 - **/software/components/metaconfig/config_updatedb**
    - Description: Override the default config file
    - */software/components/metaconfig/config_updatedb/prunefs*
        - Description: A list of file system types which should not be scanned by updatedb.
        - Optional
        - Type: string
    - */software/components/metaconfig/config_updatedb/prunenames*
        - Description: A list of directory names (without paths) which should not be scanned by updatedb.
        - Optional
        - Type: prunename
    - */software/components/metaconfig/config_updatedb/prunepaths*
        - Description: A list of path names of directories which should not be scanned by updatedb.
        - Optional
        - Type: absolute_file_path
    - */software/components/metaconfig/config_updatedb/prune_bind_mounts*
        - Description: If prune_bind_mounts is set to true, bind mounts are not scanned by updatedb.
        - Optional
        - Type: boolean
