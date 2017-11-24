
### NAME

EDG::WP4::CCM::CacheManager

### SYNOPSIS

    $cm = EDG::WP4::CCM::CacheManager->new(["/path/to/root/of/cache"]);
    $cfg = $cm->getUnlockedConfiguration($cred[, $cid]);
    $cfg = $cm->getLockedConfiguration($cred[, $cid]);
    $cfg = $cm->getAnonymousConfiguration($cred[, $cid]);
    $bool = $cm->isLocked();

### DESCRIPTION

Module provides CacheManager class. This is the top level class
of the NVA-API library. It is used by the clients to interact with
the NVA cache.

- new ($cache\_path)

    Create new CacheManager object with `$cache_path`.

    `$config_file` is an optional parameter that points
    to the CCM config file.

- getCachePath

    returns path of the cache

- getConfigurationPath

    For given `cid`, return the basepath of the Configuration data.
    (No checks are made e.g. if the directory exists,
    simply returns the directory name).

- getCids

    Return arrayref to sorted list of all found/valid CIDs.

    Returns undef in case of problem.

- getCid

    For given `cid`, validate and check the CID.

    Returns undef for a non-existing CID.

    Also handles special values for `cid`:

    - undef, "current" or empty string

        If CID is undef, the string "current" or an empty string, the current CID
        (from the "current.cid" file) is returned.

    - "latest" or "-"

        If CID is the string "latest" or "-", the latest CID
        (from the "latest.cid" file) is returned.

    - negative value (e.g. -1)

        If CID is negative `-N`, the N-th most recent CID value is returned
        (e.g. -1 returns the most recent CID, -2 the CID before the most recent, ...).

        (A distinction is made between "most recent" and "latest", as the "latest" CID
        is held in the "latest.cid" file).

- getConfiguration ($cred, $cid)

    Returns narrowest-possible Configuration object.

    If `cid` is defined, return a locked Configuration with this `cid`.
    (Special values for `cid` are handled by the `getCid` method).

    If `cid` is undefined, an unlocked Configuration is used (and the write permission
    for the anonymous flag are checked against the CacheManager's current CID).

    The Configuration instance is created with anonymous flag equal to `-1`
    (i.e. the Configuration instance will determine if the Configuration
    is anonymous or not based on the write permissions of the current process).

    The `locked` and `anonymous` flags can also be forced via named arguments (e.g.
    `<locked =` 1>> or `<anonymous =` 1>>).

    Security and `$cred` parameter meaning are not defined
    (but is kept for compatibility with other
    `get{Locked,Unlock,Anonymous}Configuration` methods).

    The configuration template name can also be passed via an
    optional named argument `name_template` (e.g. `name_template => basic`).

- getUnlockedConfiguration ($cred; $cid)

    This method is deprecated in favour of `getConfiguration`.

    Returns unlocked Configuration object.

    Unless the object is locked explicitly later by calling the `lock` method,
    `CCM::CacheManager::Element`s will always be fetched from the current CID,
    not the CID passed via `$cid`. (If the $cid parameter is omitted,
    the most recently downloaded configuration (when the cache
    was not globally locked) is returned.)

    Security and $cred parameter meaning are not defined.

- getLockedConfiguration ($cred; $cid)

    This method is deprecated in favour of `getConfiguration`.

    Returns locked Configuration object. If the $cid parameter is
    omitted, the most recently downloaded configuration (when the cache
    was not globally locked) is returned.

    Security and $cred parameter meaning are not defined.

- getAnonymousConfiguration ($cred; $cid)

    This method is deprecated in favour of `getConfiguration`.

    Returns unlocked anonymous Configuration object.

    Unless the object is locked explicitly later by calling the `lock` method,
    `CCM::CacheManager::Element`s will always be fetched from the current CID,
    not the CID passed via `$cid`. (If the $cid parameter is omitted,
    the most recently downloaded configuration (when the cache
    was not globally locked) is returned.)

    Security and $cred parameter meaning are not defined.

- isLocked ()

    Returns true if the cache is globally locked, otherwise false.

- getCurrentCid

    returns current cid (from cid file)

- getLatestCid

    returns latest cid (from cid file)
