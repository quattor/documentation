
### NAME

`NCM::Component::OpenNebula::Server` adds `OpenNebula` service configuration
support to `NCM::Component::OpenNebula`.

#### Public methods

- restart\_opennebula\_service

    Restarts `OpenNebula` service after any
    configuration change.

- detect\_opennebula\_version

    Detects `OpenNebula` version through opennebula-server probe files,
    the value gathered from the file must be untaint.

- change\_opennebula\_passwd

    Sets a new `OpenNebula` service password.

- set\_one\_service\_conf

    Sets `OpenNebula` configuration files used by
    the deamons, if the configuration file is changed the
    service must be restarted afterwards.

- is\_conf\_file\_modified

    Checks `OpenNebula` configuration file status.

- set\_one\_auth\_file

    Sets the authentication files used by
    `oneadmin` client tools.

- set\_file\_opts

    Sets filewriter options.

- set\_one\_server

    Configures `OpenNebula` server.

- set\_config\_group

    Sets `OpenNebula` configuration file group.
