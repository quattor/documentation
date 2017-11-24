
### Types

 - `/software/myproxy/myproxy_component_policies`
    - `/software/myproxy/myproxy_component_policies/renewers`
        - Optional
        - Type: string
    - `/software/myproxy/myproxy_component_policies/retrievers`
        - Optional
        - Type: string
    - `/software/myproxy/myproxy_component_policies/keyRetrievers`
        - Optional
        - Type: string
    - `/software/myproxy/myproxy_component_policies/trustedRetrievers`
        - Optional
        - Type: string
 - `/software/myproxy/myproxy_component`
    - `/software/myproxy/myproxy_component/flavor`
        - Optional
        - Type: string
    - `/software/myproxy/myproxy_component/confFile`
        - Optional
        - Type: string
    - `/software/myproxy/myproxy_component/daemonName`
        - Optional
        - Type: string
    - `/software/myproxy/myproxy_component/trustedDNs`
        - Optional
        - Type: string
    - `/software/myproxy/myproxy_component/authorizedDNs`
        - Optional
        - Type: myproxy_component_policies
    - `/software/myproxy/myproxy_component/defaultDNs`
        - Optional
        - Type: myproxy_component_policies

### Functions

 - component_myproxy_options_valid
