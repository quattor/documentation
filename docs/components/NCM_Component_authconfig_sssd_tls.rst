#########################################
NCM\::Component\::authconfig\::sssd - tls
#########################################

Types
-----

 - **/software/components/authconfig/ldap_req_checks**
 - **/software/components/authconfig/sssd_tls**
    - */software/components/authconfig/sssd_tls/cacert*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_tls/cacertdir*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_tls/cert*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_tls/key*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_tls/cipher_suite*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_tls/reqcert*
        - Required
        - Type: ldap_req_checks
        - Default value: hard
