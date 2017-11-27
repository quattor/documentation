
### Types

 - `/software/modprobe/module_type`
    - `/software/modprobe/module_type/name`
        - Optional
        - Type: string
    - `/software/modprobe/module_type/alias`
        - Optional
        - Type: string
    - `/software/modprobe/module_type/options`
        - Optional
        - Type: string
    - `/software/modprobe/module_type/install`
        - Optional
        - Type: string
    - `/software/modprobe/module_type/remove`
        - Optional
        - Type: string
    - `/software/modprobe/module_type/blacklist`
        - Optional
        - Type: string
 - `/software/modprobe/component_modprobe_type`
    - `/software/modprobe/component_modprobe_type/file`
        - Optional
        - Type: string
        - Default value: /etc/modprobe.d/quattor.conf
    - `/software/modprobe/component_modprobe_type/modules`
        - Optional
        - Type: module_type
