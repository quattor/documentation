#####################################
NCM\::Component\::gridmapdir - schema
#####################################

Types
-----

 - **/software/components/gridmapdir/gridmapdir_component**
    - */software/components/gridmapdir/gridmapdir_component/gridmapdir*
        - Required
        - Type: string
    - */software/components/gridmapdir/gridmapdir_component/poolaccounts*
        - Required
        - Type: long
        - Range: 0..0
    - */software/components/gridmapdir/gridmapdir_component/sharedGridmapdir*
        - Optional
        - Type: string
    - */software/components/gridmapdir/gridmapdir_component/owner*
        - Required
        - Type: string
        - Default value: root
    - */software/components/gridmapdir/gridmapdir_component/group*
        - Required
        - Type: string
        - Default value: root
    - */software/components/gridmapdir/gridmapdir_component/perms*
        - Required
        - Type: string
        - Default value: 0755
