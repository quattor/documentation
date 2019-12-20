##################################################
NCM\::Component\::metaconfig\::opennebula - schema
##################################################

Types
-----

 - **/software/components/metaconfig/aii_section**
    - Description: aii/opennebula.conf sections. url: OpenNebula RPC endpoint type absoluteURI as example: "url" = "https://localhost:2366/RPC2" pattern: a valid regular expression to match a VM fqdn. If the VM fqdn match the pattern the aii will use this section instead of [VM_DOMAIN]. The search proceeds through patterns from start to end, stopping at the first match found, if not [VM_DOMAIN] is used instead. And finally if [VM_DOMAIN] does not exist the aii will use [rpc] default section.
    - */software/components/metaconfig/aii_section/password*
        - Required
        - Type: string
    - */software/components/metaconfig/aii_section/user*
        - Optional
        - Type: string
    - */software/components/metaconfig/aii_section/pattern*
        - Optional
        - Type: string
    - */software/components/metaconfig/aii_section/url*
        - Optional
        - Type: type_absoluteURI
    - */software/components/metaconfig/aii_section/ca*
        - Description: set CA certificate location for SSL connections
        - Optional
        - Type: string
 - **/software/components/metaconfig/aii_opennebula_conf**
    - Description: aii/opennebula.conf sections This is a dictionary (to generate a section per rpc endpoint) of dictionaries (to include the endpoint options)
