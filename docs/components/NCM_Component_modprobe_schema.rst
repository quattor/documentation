###################################
NCM\::Component\::modprobe - schema
###################################

Types
-----

 - **/software/components/modprobe/module_type**
    - */software/components/modprobe/module_type/name*
        - Required
        - Type: string
    - */software/components/modprobe/module_type/alias*
        - Optional
        - Type: string
    - */software/components/modprobe/module_type/options*
        - Optional
        - Type: string
    - */software/components/modprobe/module_type/install*
        - Optional
        - Type: string
    - */software/components/modprobe/module_type/remove*
        - Optional
        - Type: string
    - */software/components/modprobe/module_type/blacklist*
        - Optional
        - Type: string
 - **/software/components/modprobe/component_modprobe_type**
    - */software/components/modprobe/component_modprobe_type/file*
        - Required
        - Type: string
        - Default value: /etc/modprobe.d/quattor.conf
    - */software/components/modprobe/component_modprobe_type/modules*
        - Required
        - Type: module_type
