
### NAME

NCM::syslog - adding entries and editing `/etc/syslog.conf`

### RESOURCES

- `/software/components/syslog/active` : boolean

    Activates/deactivates the component.

- `/software/components/syslog/fullcontrol` : boolean

    Determines whether component has full control over `/etc/syslog.conf`,
    eventually erasing entries from other sources, or whether entries
    from other sources are kept.

- `/software/components/syslog/syslogdoptions` : string

    Options for syslogd `/etc/sysconfig/syslog`

- `/software/components/syslog/syslogdoptions` : string

    Options for the klogd `/etc/sysconfig/syslog`

- `/software/components/syslog/config/`

    The configuration items.
