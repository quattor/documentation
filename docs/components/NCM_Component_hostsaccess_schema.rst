######################################
NCM\::Component\::hostsaccess - schema
######################################

Types
-----

 - **/software/components/hostsaccess/structure_hostsaccess_entry**
    - */software/components/hostsaccess/structure_hostsaccess_entry/daemon*
        - Optional
        - Type: string
    - */software/components/hostsaccess/structure_hostsaccess_entry/host*
        - Optional
        - Type: string
 - **/software/components/hostsaccess/component_hostsaccess**
    - */software/components/hostsaccess/component_hostsaccess/allow*
        - Optional
        - Type: structure_hostsaccess_entry
    - */software/components/hostsaccess/component_hostsaccess/deny*
        - Optional
        - Type: structure_hostsaccess_entry
