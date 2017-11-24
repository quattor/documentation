
### Types

 - `/software/lcas/lcas_component_plainfile_content`
    - `/software/lcas/lcas_component_plainfile_content/path`
        - Optional
        - Type: string
    - `/software/lcas/lcas_component_plainfile_content/noheader`
        - Optional
        - Type: boolean
        - Default value: false
    - `/software/lcas/lcas_component_plainfile_content/content`
        - Optional
        - Type: string
 - `/software/lcas/lcas_component_modulespec`
    - `/software/lcas/lcas_component_modulespec/path`
        - Optional
        - Type: string
    - `/software/lcas/lcas_component_modulespec/args`
        - Optional
        - Type: string
    - `/software/lcas/lcas_component_modulespec/conf`
        - Optional
        - Type: lcas_component_plainfile_content
 - `/software/lcas/lcas_component_db`
    - `/software/lcas/lcas_component_db/path`
        - Optional
        - Type: string
    - `/software/lcas/lcas_component_db/module`
        - Optional
        - Type: lcas_component_modulespec
 - `/software/lcas/lcas_component`
    - `/software/lcas/lcas_component/db`
        - Optional
        - Type: lcas_component_db
    - `/software/lcas/lcas_component/dbpath`
        - Optional
        - Type: string
    - `/software/lcas/lcas_component/module`
        - Optional
        - Type: lcas_component_modulespec

### Functions

 - component_lcas_valid
