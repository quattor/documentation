
### NAME

NCM::Component::Systemd::Service handles the [systemd](../components/systemd.md) units.

#### Public methods

- new

    Returns a new object, accepts the following options

    - log

        A logger instance (compatible with `CAF::Object`).

- configure

    `configure` gathered the to-be-configured units from the `config` using the
    `gather_units` method and then takes appropriate actions.

#### Private methods

- set\_unconfigured\_default

    Set the default behaviour for unconfigured units from `ncn-systemd`
    and legacy [chkconfig](../components/chkconfig.md).

- gather\_configured\_units

    Gather the list of all configured units from both `ncm-systemd`
    and legacy [chkconfig](../components/chkconfig.md) location, and take appropriate actions.

    For any unit defined in both [systemd](../components/systemd.md) and [chkconfig](../components/chkconfig.md) location,
    the [systemd](../components/systemd.md) settings will be used.

    Returns a hash reference with key the unit name and value the unit detail.

- gather\_current\_units

    Gather list of current units from both `systemctl` and legacy `chkconfig`
    using resp. `unit` and [chkconfig](../components/chkconfig.md) `current_units` methods.

    The hashref `relevant_units` is used to run minimal set
    of system commands where possible: e.g. if the hashref represents the
    configured units and if `unconfigured_default` is `ignore`, only gathered
    details for these units.

- process

    `process` the `configured` units and
    retrun hash references with state and activation changes.

    It uses the `current` units to make the required decisions.

    (Unconfigured units are not dealt with in this method).

- change

    Actually make the changes as specified in
    the hashrefs `states` and `acts` (which hold the
    changes to be made to resp. the state and the activity
    of the units).
