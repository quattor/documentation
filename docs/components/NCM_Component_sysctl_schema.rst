#################################
NCM\::Component\::sysctl - schema
#################################

Types
-----

 - **/software/components/sysctl/component_sysctl_structure**
    - */software/components/sysctl/component_sysctl_structure/command*
        - Required
        - Type: string
        - Default value: /sbin/sysctl
    - */software/components/sysctl/component_sysctl_structure/compat-v1*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/sysctl/component_sysctl_structure/confFile*
        - Required
        - Type: string
        - Default value: /etc/sysctl.conf
    - */software/components/sysctl/component_sysctl_structure/variables*
        - Optional
        - Type: string
