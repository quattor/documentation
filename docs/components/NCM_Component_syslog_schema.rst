#################################
NCM\::Component\::syslog - schema
#################################

Types
-----

 - **/software/components/syslog/component_syslog_selector_type**
    - */software/components/syslog/component_syslog_selector_type/facility*
        - Required
        - Type: string
    - */software/components/syslog/component_syslog_selector_type/priority*
        - Required
        - Type: string
 - **/software/components/syslog/component_syslog_legacy_rule**
    - */software/components/syslog/component_syslog_legacy_rule/selector*
        - Optional
        - Type: component_syslog_selector_type
    - */software/components/syslog/component_syslog_legacy_rule/action*
        - Required
        - Type: string
    - */software/components/syslog/component_syslog_legacy_rule/template*
        - Optional
        - Type: string
    - */software/components/syslog/component_syslog_legacy_rule/comment*
        - Optional
        - Type: string
 - **/software/components/syslog/syslog_component**
    - */software/components/syslog/syslog_component/config*
        - Required
        - Type: component_syslog_legacy_rule
    - */software/components/syslog/syslog_component/directives*
        - Optional
        - Type: string
    - */software/components/syslog/syslog_component/daemontype*
        - Required
        - Type: string
        - Default value: syslog
    - */software/components/syslog/syslog_component/file*
        - Description: Configuration filename. Defaults to /etc/<daemontype>.conf.
        - Optional
        - Type: string
    - */software/components/syslog/syslog_component/syslogdoptions*
        - Description: Options for syslogd /etc/sysconfig/(r)syslog (will be wrapped in double quotes if needed)
        - Optional
        - Type: string
    - */software/components/syslog/syslog_component/klogdoptions*
        - Description: Options for the klogd /etc/sysconfig/(r)syslog (will be wrapped in double quotes if needed)
        - Optional
        - Type: string
    - */software/components/syslog/syslog_component/fullcontrol*
        - Description: Determines whether component has full control over the configuration file, eventually erasing entries from other sources. If false or not defined, entries from other sources are kept and configuration entries are added.
        - Optional
        - Type: boolean
