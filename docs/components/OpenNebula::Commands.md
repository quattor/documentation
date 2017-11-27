
### NAME

`NCM::Component::OpenNebula::Commands` Configuration module for ONE

### DESCRIPTION

Configuration module for OpenNebula. Executes the required ssh commands
to enable the hosts to be used by the cloud server.

This component needs a 'oneadmin' user.
The user should be able to run these commands with sudo without password:

- `virsh secret-define --file `/var/lib/one/templates/secret/secret_ceph.xml``
- `virsh secret-set-value --secret $uuid --base64 $secret`

#### Public methods

- set\_ssh\_command

    Sets `$sshcmd`.

- run\_command

    Executes a command and return the output.
    Returns sdout and stderr array.

- run\_virsh\_as\_oneadmin\_with\_ssh

    Executes a command prefixed with `virsh` and returns the output.

- run\_oneuser\_as\_oneadmin\_with\_ssh

    Executes `oneuser` command and returns the output.

- run\_onehost\_as\_oneadmin\_with\_ssh

    Executes `onehost` command to sync hosts VMMs scripts.

- has\_shell\_escapes

    Checks for shell escapes.

- run\_command\_as\_oneadmin

    Executes a command as `oneadmin` user.

- run\_command\_as\_oneadmin\_with\_ssh

    Executes a command as `oneadmin` over ssh, optionally with options.

- ssh\_known\_keys

    Accepts and adds unknown keys if wanted.

- can\_connect\_to\_host

    Checks if the host is reachable or not.
