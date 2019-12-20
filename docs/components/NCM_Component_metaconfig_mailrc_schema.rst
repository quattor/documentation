##############################################
NCM\::Component\::metaconfig\::mailrc - schema
##############################################

Types
-----

 - **/software/components/metaconfig/mailrc_element**
    - */software/components/metaconfig/mailrc_element/smtp*
        - Optional
        - Type: string
    - */software/components/metaconfig/mailrc_element/from*
        - Optional
        - Type: type_email
    - */software/components/metaconfig/mailrc_element/smtp-use-starttls*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/mailrc_element/smtp-auth-user*
        - Optional
        - Type: string
    - */software/components/metaconfig/mailrc_element/smtp-auth-password*
        - Optional
        - Type: string
    - */software/components/metaconfig/mailrc_element/nss-config-dir*
        - Optional
        - Type: string
 - **/software/components/metaconfig/mailrc_config**
    - */software/components/metaconfig/mailrc_config/account*
        - Optional
        - Type: mailrc_element
