
### NAME

NCM::Component::Systemd::Service::Unit is a class handling services with units

#### Public methods

- new

    Returns a new object, accepts the following options

    - log

        A logger instance (compatible with `CAF::Object`).

- unit\_text

    Convert unit `detail` hashref to human readable string.

    Generates errors for missing attributes.

- current\_units

    Return hash reference with current units
    determined via `make_cache_alias`.

    The array references `units` and `possible_missing`
    are passed to `make_cache_alias`.

- current\_target

    Return the current target.

    TODO: implement this. systemctl list-units --type target
    lists all current targets (yes, with an s).

- default\_target

    Return the default target.

    Supported options:

    - force

        Force is passed to the `fill_cache` method.

- configured\_units

    `configured_units` parses the `tree` hash reference and builds up the
    units to be configured. It returns a hash reference with key the unit name and
    values the details of the unit.

    Units with missing types are assumed to be TYPE\_SERVICE; targets with
    missing type are assumed to be TYPE\_TARGET.

    (`tree` is typcially obtained with the `_getTree` method).

- get\_aliases

    Given an arrayref of `units`, return a hashref with key the unit (from the list)
    that is an alias for another unit (not necessarily from the list);
    and the other unit's name is the value.

    The `unit_alias` cache is used for lookup.

    The `possible_missing` arrayref is passed to the `fill_cache` method

    Supported options

    - force

        The force flag is passed to the `fill_cache` method

    - possible\_missing

        The `possible_missing` arrayref is passed to `make_cache_alias`.

- possible\_missing

    Given the hashref `units` with key unit and value the unit's details,
    return a array ref with units that are "possible missing".
    Such units will not cause an error to be logged if they are not
    found in the cache during certain methods (e.g. `make_cache_alias`).

#### Private methods

- is\_possible\_missing

    Determine if `unit` is `possible_missing`
    (see `make_cache_alias`). (Returns 0 or 1).

    A unit is possible\_missing if

    - the unit is in state masked (i.e. unit that is not expected
    to be running anyway). Unit in state disabled is not "possible missing"
    (they can be dependency for other units).

- init\_cache

    (Re)Initialise all unit caches.

    Returns the caches (for unittestung mainly).

    Affected caches are

    - unit\_cache
    - unit\_alias
    - dependency\_cache

- get\_type\_shortname

    `get_type_shortname` returns the type and shortname based on the
    `unit` and optional `type`.

    If the `type` is not specified, it will be derived using the supported types.

    If the type can't be determined based on the supported types,
    the `defaulttype` will be used. If in this case the `defaulttype`
    is undefined, DEFAULT\_TYPE will be used and error will be logged.
    If the `defaulttype` is defined,

- make\_cache\_alias

    (Re)generate the `unit_cache` and `unit_alias` map
    based on current units and unitfiles from the `systemctl_list_units`
    and `systemctl_list_unit_files` methods.

    Details for each unit from arrayref `units` are also added.
    If `units` is empty/undef, all found units and unitfiles
    are.

    If a unit is an alias of an other unit, it is added to the alias map.
    Each non-alias unit is also added as it's own alias.

    Units in the `possible_missing` arrayref can be missing, and no error
    is logged if they are. For any other unit, an error is logged when
    neither the `systemctl_list_units`
    and `systemctl_list_unit_files` methods provide any information about it.

    Returns the generated cache and alias map for unittesting purposes.

- fill\_cache

    Fill the `unit_cache` and `unit_alias map`
    for the arrayref `units` provided.

    The cache is updated via the `make_cache_alias` method if the unit
    is missing from the unit\_alias map or if `force` is true.

    Supported options

    - force

        Force cache refresh.

    - possible\_missing

        The `possible_missing` arrayref is passed to `make_cache_alias`.

- get\_unit\_show

    Return the show `property` for `unit` from the
    unit\_cache and unit\_alias map.

    Supported options

    - force

        Force cache refresh.

    - possible\_missing

        If true, this unit is "possible missing" (see `make_cache_alias`)

- get\_wantedby

    Return a hashref of all units that "want" `unit`
    (hashref is used for easy lookup; the key is the unit,
    the value is a boolean).

    It uses the `dependency_cache` for reverse dependencies
    (missing cache entries are added).

    Supported options

    - force

        Force cache update.

    - ignoreself

        By default, the reverse dependency list contains the unit itself too.
        With `ignoreself` true, the unit itself is not returned
        (but still stored in cache).

- is\_wantedby

    Return if `unit` is wanted by `target`.

    Any unit can be passed as `target` (it does not have to be
    a unit of type 'target').

    It uses the `get_wantedby` method for the dependency lookup.

    Supported options

    - force

        Force cache update (passed to `get_wantedby`).

- is\_active

    `is_active` returns true or false and reflects if a unit is "running" or not.

    The following options are supported

    - sleeptime
    =item max

        Units that are 'reloading', 'activating' and 'deactivating' are refreshed with
        `sleep` (default 1 sec) and `max` number of tries (default 3). Until

    - force

        Force cache refresh (passed to `get_unit_show`).

- get\_ufstate

    Return the state of the `unit` using the UnitFileState and
    the derived state from the state of the $PROPERTY\_WANTEDBY units.

    The returned state can be more then the usual supported states (e.g. static).

    The following options are supported

    - force

        Force cache refresh (passed to `get_unit_show` and `fill_cache`)

- is\_ufstate

    `is_ufstate` returns true or false if the
    UnitFileState of `unit` matches the (simplified) `state`.

    An error is logged  and undef returned if the unit can't be queried.

    The following options are supported

    - force

        Refresh the cache `force` (passed to `get_ufstate` method).

#### Private methods

- \_getTree

    The `getTree` method is similar to the regular
    **EDG::WP4::CCM::CacheManager::Element::getTree**, except that
    it keeps the unitfile configuration as an Element instance
    (as required by **NCM::Component::Systemd::UnitFile**).

    It takes as arguments a **EDG::WP4::CCM::CacheManager::Configuration** instance
    `$config` and a `$path` to the root of the whole unit tree.
