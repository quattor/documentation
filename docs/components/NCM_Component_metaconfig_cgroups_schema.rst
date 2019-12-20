###############################################
NCM\::Component\::metaconfig\::cgroups - schema
###############################################

Types
-----

 - **/software/components/metaconfig/cgroups_cgrule_user**
    - */software/components/metaconfig/cgroups_cgrule_user/name*
        - Optional
        - Type: string
    - */software/components/metaconfig/cgroups_cgrule_user/group*
        - Optional
        - Type: string
    - */software/components/metaconfig/cgroups_cgrule_user/ditto*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cgroups_cgrule_user/any*
        - Optional
        - Type: boolean
 - **/software/components/metaconfig/cgroups_controller**
 - **/software/components/metaconfig/cgroups_cgrule**
    - Description: Type for a single cgrule. Contents should be a list of these.
    - */software/components/metaconfig/cgroups_cgrule/user*
        - Required
        - Type: cgroups_cgrule_user
    - */software/components/metaconfig/cgroups_cgrule/process*
        - Optional
        - Type: string
    - */software/components/metaconfig/cgroups_cgrule/controllers*
        - Required
        - Type: cgroups_controller
    - */software/components/metaconfig/cgroups_cgrule/destination*
        - Required
        - Type: string
 - **/software/components/metaconfig/cgroups_cgconfig_permissions_task**
    - */software/components/metaconfig/cgroups_cgconfig_permissions_task/uid*
        - Optional
        - Type: defined_user
    - */software/components/metaconfig/cgroups_cgconfig_permissions_task/gid*
        - Optional
        - Type: defined_group
    - */software/components/metaconfig/cgroups_cgconfig_permissions_task/fperm*
        - Optional
        - Type: string
 - **/software/components/metaconfig/cgroups_cgconfig_permissions_admin**
    - */software/components/metaconfig/cgroups_cgconfig_permissions_admin/dperm*
        - Optional
        - Type: string
 - **/software/components/metaconfig/cgroups_cgconfig_permissions**
    - */software/components/metaconfig/cgroups_cgconfig_permissions/task*
        - Optional
        - Type: cgroups_cgconfig_permissions_task
    - */software/components/metaconfig/cgroups_cgconfig_permissions/admin*
        - Optional
        - Type: cgroups_cgconfig_permissions_admin
 - **/software/components/metaconfig/cgroups_cgconfig_mount**
 - **/software/components/metaconfig/cgroups_cgconfig_controllers**
 - **/software/components/metaconfig/cgroups_cgconfig_group**
    - */software/components/metaconfig/cgroups_cgconfig_group/perm*
        - Optional
        - Type: cgroups_cgconfig_permissions
    - */software/components/metaconfig/cgroups_cgconfig_group/controllers*
        - Optional
        - Type: cgroups_cgconfig_controllers
 - **/software/components/metaconfig/cgroups_cgconfig_default**
    - */software/components/metaconfig/cgroups_cgconfig_default/perm*
        - Optional
        - Type: cgroups_cgconfig_permissions
 - **/software/components/metaconfig/cgroups_cgconfig_service**
    - */software/components/metaconfig/cgroups_cgconfig_service/mount*
        - Optional
        - Type: cgroups_cgconfig_mount
    - */software/components/metaconfig/cgroups_cgconfig_service/group*
        - Optional
        - Type: cgroups_cgconfig_group
    - */software/components/metaconfig/cgroups_cgconfig_service/template*
        - Optional
        - Type: cgroups_cgconfig_group
    - */software/components/metaconfig/cgroups_cgconfig_service/default*
        - Optional
        - Type: cgroups_cgconfig_default

Functions
---------

 - is_cgroups_controller
    - Description: controllers from /proc/cgroups or named hierarchy
