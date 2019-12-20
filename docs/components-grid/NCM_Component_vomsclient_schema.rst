#####################################
NCM\::Component\::vomsclient - schema
#####################################

Types
-----

 - **/software/components/vomsclient/structure_vomsclient_voms_info**
    - */software/components/vomsclient/structure_vomsclient_voms_info/name*
        - Description: The complete name of the VO, if the 'vos' key is an alias name. This property is deprecated : it is recommended to use the complete name of the VO as 'vos' key.
        - Optional
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/host*
        - Description: The complete hostname of the VOMS server.
        - Required
        - Type: type_fqdn
    - */software/components/vomsclient/structure_vomsclient_voms_info/port*
        - Description: The port number of the VOMS server.
        - Required
        - Type: type_port
    - */software/components/vomsclient/structure_vomsclient_voms_info/cert*
        - Description: The certificate for the server.
        - Required
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/oldcert*
        - Description: The expiring certificate for the server. This allows smooth transition between 2 certificates.
        - Optional
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/DN*
        - Description: DN of VOMS server certificate.
        - Optional
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/issuer*
        - Description: DN of VOMS server certificate issuer.
        - Optional
        - Type: string
 - **/software/components/vomsclient/vomsclient_component**
    - */software/components/vomsclient/vomsclient_component/lscfile*
        - Description: Use LSC format instead of certificate to configure vomsCertsDir.
        - Optional
        - Type: boolean
    - */software/components/vomsclient/vomsclient_component/vomsCertsDir*
        - Description: The directory to write the VOMS server certificates into. If the directory doesn't exist, it is created. It will remove all managed files and create new ones each time the configuration is done.
        - Optional
        - Type: string
    - */software/components/vomsclient/vomsclient_component/vomsServersDir*
        - Description: The directory to write the VOMS server parameters into. If the directory doesn't exist, it is created. It will remove all managed file and create new ones each time the configuration is done.
        - Optional
        - Type: string
    - */software/components/vomsclient/vomsclient_component/vos*
        - Description: This is a named list of VOMS VO information. Each key should be the VO name. The value is a list of dict: each dict describes one VOMS server supporting the VO.
        - Optional
        - Type: structure_vomsclient_voms_info
