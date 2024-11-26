###############################
NCM\::Component\::ipmi - schema
###############################

Types
-----

 - **/software/components/ipmi/structure_users**
    - */software/components/ipmi/structure_users/login*
        - Description: User Name String in ASCII (16 bytes) See IPMI Spec v2.0 rev 1.1 section 22.28 Set User Name Command Restricted to only printable ASCII characters
        - Required
        - Type: string_trimmed
    - */software/components/ipmi/structure_users/password*
        - Description: Password String in ASCII (16/20 bytes) See IPMI Spec v2.0 rev 1.1 section 22.30 Set User Password Command Restricted to only printable ASCII characters
        - Required
        - Type: string_trimmed
    - */software/components/ipmi/structure_users/priv*
        - Description: Channel Privilege Level Limit (4 bits) See IPMI Spec v2.0 rev 1.1 section 22.26 Set User Access Command Standard Levels: 0 = Reserved (not supported) 1 = CALLBACK 2 = USER 3 = OPERATOR 4 = ADMINISTRATOR 5 = OEM Proprietary 15 = No access
        - Optional
        - Type: long
        - Range: 1..15
    - */software/components/ipmi/structure_users/userid*
        - Description: Numeric User ID (6 bits) Standard values: 0 = Reserved (not supported) 1 = The null user
        - Optional
        - Type: long
        - Range: 1..63
 - **/software/components/ipmi/component_ipmi_type**
    - */software/components/ipmi/component_ipmi_type/channel*
        - Description: Channel Number (4 bits) See IPMI Spec v2.0 rev 1.1 section 6.3 Channel Numbers Standard Channels: 0 Primary IPMB (not supported) 1-11 Implementation-specific (normal range) 12-13 Reserved (not supported) 14 Reserved for identifying current channel (not supported) 15 System Interface (not supported)
        - Required
        - Type: long
        - Range: 1..11
        - Default value: 1
    - */software/components/ipmi/component_ipmi_type/users*
        - Description: User Configuration List of structure_users type.
        - Required
        - Type: structure_users
