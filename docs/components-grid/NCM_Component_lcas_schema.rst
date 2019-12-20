###############################
NCM\::Component\::lcas - schema
###############################

Types
-----

 - **/software/components/lcas/lcas_component_plainfile_content**
    - */software/components/lcas/lcas_component_plainfile_content/path*
        - Required
        - Type: string
    - */software/components/lcas/lcas_component_plainfile_content/noheader*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/lcas/lcas_component_plainfile_content/content*
        - Optional
        - Type: string
 - **/software/components/lcas/lcas_component_modulespec**
    - */software/components/lcas/lcas_component_modulespec/path*
        - Required
        - Type: string
    - */software/components/lcas/lcas_component_modulespec/args*
        - Optional
        - Type: string
    - */software/components/lcas/lcas_component_modulespec/conf*
        - Optional
        - Type: lcas_component_plainfile_content
 - **/software/components/lcas/lcas_component_db**
    - */software/components/lcas/lcas_component_db/path*
        - Required
        - Type: string
    - */software/components/lcas/lcas_component_db/module*
        - Optional
        - Type: lcas_component_modulespec
 - **/software/components/lcas/lcas_component**
    - */software/components/lcas/lcas_component/db*
        - Optional
        - Type: lcas_component_db
    - */software/components/lcas/lcas_component/dbpath*
        - Optional
        - Type: string
    - */software/components/lcas/lcas_component/module*
        - Optional
        - Type: lcas_component_modulespec

Functions
---------

 - component_lcas_valid
