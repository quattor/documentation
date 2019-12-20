##########################################
NCM\::Component\::authconfig\::sssd - sasl
##########################################

Types
-----

 - **/software/components/authconfig/sssd_sasl**
    - */software/components/authconfig/sssd_sasl/mech*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_sasl/authid*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_sasl/realm*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_sasl/canonicalize*
        - Optional
        - Type: boolean
    - */software/components/authconfig/sssd_sasl/minssf*
        - Optional
        - Type: long
 - **/software/components/authconfig/sssd_krb5**
    - */software/components/authconfig/sssd_krb5/keytab*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_krb5/init_creds*
        - Optional
        - Type: boolean
    - */software/components/authconfig/sssd_krb5/ticket_lifetime*
        - Optional
        - Type: long
