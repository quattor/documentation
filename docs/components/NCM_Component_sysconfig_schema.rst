####################################
NCM\::Component\::sysconfig - schema
####################################

Types
-----

 - **/software/components/sysconfig/component_sysconfig_file**
    - Description: Contents of a sysconfig file modelled as a dict of key-value pairs. Two reserved keys `prologue` and `epilogue` are treated specially, their values will be copied verbatim into the file before or after the key-pair definitions. Example: '/software/components/sysconfig/files/scfg' = dict( 'epilogue', 'export LANG=C', 'KEY', 'VALUE', ); This will create the file `/etc/sysconfig/scfg` which contains: KEY=VALUE export LANG=C
 - **/software/components/sysconfig/component_sysconfig**
    - */software/components/sysconfig/component_sysconfig/files*
        - Description: dict of dicts with a file name as the first key and the contents of each file as the child dict.
        - Optional
        - Type: component_sysconfig_file
