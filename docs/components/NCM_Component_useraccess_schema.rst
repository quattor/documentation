#####################################
NCM\::Component\::useraccess - schema
#####################################

Types
-----

 - **/software/components/useraccess/useraccess_pointer**
 - **/software/components/useraccess/useraccess_kerberos**
    - */software/components/useraccess/useraccess_kerberos/realm*
        - Required
        - Type: type_hostname
    - */software/components/useraccess/useraccess_kerberos/principal*
        - Required
        - Type: string
    - */software/components/useraccess/useraccess_kerberos/instance*
        - Optional
        - Type: string
    - */software/components/useraccess/useraccess_kerberos/host*
        - Optional
        - Type: type_hostname
 - **/software/components/useraccess/credentialfilestring**
 - **/software/components/useraccess/useraccess_auth**
    - */software/components/useraccess/useraccess_auth/ssh_keys_urls*
        - Optional
        - Type: type_absoluteURI
    - */software/components/useraccess/useraccess_auth/kerberos4*
        - Optional
        - Type: useraccess_kerberos
    - */software/components/useraccess/useraccess_auth/kerberos5*
        - Optional
        - Type: useraccess_kerberos
    - */software/components/useraccess/useraccess_auth/acls*
        - Optional
        - Type: string
    - */software/components/useraccess/useraccess_auth/roles*
        - Optional
        - Type: useraccess_pointer
    - */software/components/useraccess/useraccess_auth/ssh_keys*
        - Optional
        - Type: string
    - */software/components/useraccess/useraccess_auth/managed_credentials*
        - Required
        - Type: credentialfilestring
 - **/software/components/useraccess/useraccess_component**
    - */software/components/useraccess/useraccess_component/configSerial*
        - Optional
        - Type: string
    - */software/components/useraccess/useraccess_component/users*
        - Required
        - Type: useraccess_auth
    - */software/components/useraccess/useraccess_component/roles*
        - Optional
        - Type: useraccess_auth
    - */software/components/useraccess/useraccess_component/acl_services*
        - Optional
        - Type: string
