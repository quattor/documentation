
### NAME

NCM::Component::Systemd::UnitFile handles the configuration of [systemd](../components/systemd.md) unitfiles.

#### Public methods

- new

    Returns a new object, accepts the following mandatory arguments

    - unit

        The unit (full `name.type`).

    - config

        A `EDG::WP4::CCM::CacheManager::Element` instance with the unitfile configuration.

        (An element instance is required becasue the rendering of
        the configuration is pan-basetype sensistive).

    and options

    - replace

        A boolean to replace the configuration. (Default/undef is false).

        For a non-replaced configuration, a directory
        `</etc/systemd/system/<unit`.d>> is created
        and the unitfile is `</etc/systemd/system/<unit`.d/quattor.conf>>.
        Systemd will pickup settings from this `quattor.conf` and other `.conf` files
        in this directory,
        and also any configuration for the unit in the default systemd paths (e.g. typical
        unit part of the software package located in
        `</lib/systemd/system/<unit`>>).

        A replaced configuration overrides all existing system unitfiles
        for the unit (and has to define all attributes). It has filename
        `</etc/systemd/system/<unit`>>.

    - backup

        Backup files and/or directories.

    - custom

        A hashref with custom configuration data. See `custom` method.

    - log

        A logger instance (compatible with `CAF::Object`).

- custom

    The `custom` method prepares configuration data that is cannot be
    found in the profile.

    Report hashref with custom data on success, undef otherwise.

    Following custom attributes are supported:

    - CPUAffinity

        Obtain the `systemd.exec` `CPUAffinity` list determined via `hwloc(7)` locations.

        Allows to e.g. cpubind on numanodes using the `node:X` location

        Forces an empty list to reset any possible previously defined affinity.

- write

    Create the unitfile. Returns undef in case of problem,
    a boolean indication if something changed otherwise.

    (This method will take all required actions to use the values, like
    reloading the systemd daemon.
    It will not however change the state of the unit,
    e.g. by restarting it.)

#### Private methods

- \_prepare\_path

    Create and return the filename to use,
    and prepare the directory structure if needed.

    `basedir` is the base directory to use, e.g. `$UNITFILE_DIRECTORY`.

- \_hwloc\_calc\_cpuaffinity

    Run `_hwloc_calc_cpus`, and returns in `CPUAffinity` format with a reset

- \_hwloc\_calc\_cpus

    Run the `hwloc-calc --physical --intersect PU` command for `locations`.

    Returns arrayref with CPU indices on success, undef otherwise.

- \_make\_variables\_custom

    A function that return the custom variables hashref to pass as ttoptions.
    (This is a function, not a method).
