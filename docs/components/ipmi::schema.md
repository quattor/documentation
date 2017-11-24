
### Types

 - `/software/ipmi/structure_users`
    - `/software/ipmi/structure_users/login`
        - Optional
        - Type: string
    - `/software/ipmi/structure_users/password`
        - Optional
        - Type: string
    - `/software/ipmi/structure_users/priv`
        - Optional
        - Type: string
    - `/software/ipmi/structure_users/userid`
        - Optional
        - Type: long
 - `/software/ipmi/component_ipmi_type`
    - `/software/ipmi/component_ipmi_type/channel`
        - Optional
        - Type: long
        - Default value: 1
    - `/software/ipmi/component_ipmi_type/users`
        - Optional
        - Type: structure_users
    - `/software/ipmi/component_ipmi_type/net_interface`
        - Optional
        - Type: string
