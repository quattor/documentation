######################
aii\::freeipa\::schema
######################

Types
-----

 - **aii_freeipa**
    - *aii_freeipa/module*
        - Required
        - Type: string
    - *aii_freeipa/remove*
        - Description: remove the host on AII removal (precedes disable)
        - Required
        - Type: boolean
        - Default value: false
    - *aii_freeipa/disable*
        - Description: disable the host on AII removal
        - Required
        - Type: boolean
        - Default value: true

Variables
---------

 - FREEIPA_AII_MODULE_NAME

Functions
---------

 - validate_aii_freeipa_hooks
    - Description: a function to validate all freeipa hooks example usage: bind "/system/aii/hooks" = dict with validate_aii_freeipa_hooks('post_reboot')
