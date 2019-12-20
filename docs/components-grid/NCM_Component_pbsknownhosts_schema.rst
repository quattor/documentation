########################################
NCM\::Component\::pbsknownhosts - schema
########################################

Types
-----

 - **/software/components/pbsknownhosts/pbsknownhosts_component**
    - */software/components/pbsknownhosts/pbsknownhosts_component/configFile*
        - Required
        - Type: string
        - Default value: /opt/edg/etc/edg-pbs-knownhosts.conf
    - */software/components/pbsknownhosts/pbsknownhosts_component/pbsbin*
        - Required
        - Type: string
        - Default value: /usr/bin
    - */software/components/pbsknownhosts/pbsknownhosts_component/nodes*
        - Required
        - Type: string
    - */software/components/pbsknownhosts/pbsknownhosts_component/keytypes*
        - Required
        - Type: string
        - Default value: rsa1,rsa,dsa
    - */software/components/pbsknownhosts/pbsknownhosts_component/knownhosts*
        - Required
        - Type: string
        - Default value: /etc/ssh/ssh_known_hosts
    - */software/components/pbsknownhosts/pbsknownhosts_component/knownhostsscript*
        - Optional
        - Type: string
    - */software/components/pbsknownhosts/pbsknownhosts_component/targets*
        - Optional
        - Type: string
    - */software/components/pbsknownhosts/pbsknownhosts_component/shostsConfigFile*
        - Optional
        - Type: string
    - */software/components/pbsknownhosts/pbsknownhosts_component/shosts*
        - Optional
        - Type: string
    - */software/components/pbsknownhosts/pbsknownhosts_component/shostsscript*
        - Optional
        - Type: string
