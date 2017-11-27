
### Types

 - `/software/freeipa/aii_freeipa`
    - `/software/freeipa/aii_freeipa/module`
        - Optional
        - Type: string
    - `/software/freeipa/aii_freeipa/remove`
        - Description: remove the host on AII removal (precedes disable)
        - Optional
        - Type: boolean
        - Default value: false
    - `/software/freeipa/aii_freeipa/disable`
        - Description: disable the host on AII removal
        - Optional
        - Type: boolean
        - Default value: true

### Functions

 - validate_aii_freeipa_hooks
    - Description: 
a function to validate all freeipa hooks
example usage:
    bind "/system/aii/hooks" = dict with validate_aii_freeipa_hooks('post_reboot')

