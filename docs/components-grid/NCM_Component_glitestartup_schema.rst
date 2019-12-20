#######################################
NCM\::Component\::glitestartup - schema
#######################################

Types
-----

 - **/software/components/glitestartup/glitestartup_component_service**
    - */software/components/glitestartup/glitestartup_component_service/args*
        - Optional
        - Type: string
 - **/software/components/glitestartup/glitestartup_component_post_restart**
    - */software/components/glitestartup/glitestartup_component_post_restart/cmd*
        - Required
        - Type: string
    - */software/components/glitestartup/glitestartup_component_post_restart/expectedStatus*
        - Optional
        - Type: long
 - **/software/components/glitestartup/glitestartup_component**
    - */software/components/glitestartup/glitestartup_component/configFile*
        - Required
        - Type: string
        - Default value: /opt/glite/etc/gLiteservices
    - */software/components/glitestartup/glitestartup_component/initScript*
        - Required
        - Type: string
        - Default value: /etc/rc.d/init.d/gLite
    - */software/components/glitestartup/glitestartup_component/disableOutput*
        - Optional
        - Type: boolean
    - */software/components/glitestartup/glitestartup_component/disableError*
        - Optional
        - Type: boolean
    - */software/components/glitestartup/glitestartup_component/restartEnv*
        - Optional
        - Type: string
    - */software/components/glitestartup/glitestartup_component/postRestart*
        - Optional
        - Type: glitestartup_component_post_restart
    - */software/components/glitestartup/glitestartup_component/restartServices*
        - Optional
        - Type: boolean
    - */software/components/glitestartup/glitestartup_component/createProxy*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/glitestartup/glitestartup_component/scriptPaths*
        - Required
        - Type: string
    - */software/components/glitestartup/glitestartup_component/services*
        - Required
        - Type: glitestartup_component_service
