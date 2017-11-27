
### NAME

EDG::WP4::CCM::CacheManager::Configuration - Configuration class

### SYNOPSIS

    $cid = $cfg->getConfigurationId();
    $elt = $cfg->getElement($path);
    $elt = $cfg->getElement($string);
    $val = $cfg->getValue($path);
    $val = $cfg->getValue($string);
    $bool = $cfg->elementExists($path);
    $bool = $cfg->elementExists($string);
    $cfg->lock();
    $cfg->unlock();
    $bool = $cfg->isLocked();

### DESCRIPTION

Module provides the Configuration class, to manipulate confgurations.

- new

    Create Configuration object. It takes three arguments:
        `cache_manager`: the CacheManager object
        `cid`: the configuration id
        `locked`: boolean lock flag
        `anonymous`: boolean anonymous flag
        `name_template`: name template

    If a configuration with specified CID does not exists, an exception is
    thrown.

    When the `locked` flag is set (or when the `lock` method is called to set it),
    the Configuration instance is bound to the specific CID, even if this is not
    the CacheManager's current one (e.g. when a new profile is fetched during the lifetime
    of the process, the CacheManager current CID is updated to the latest one).
    The locking is relevant when a [CacheManager::Element](../CCM/CacheManager::Element.md) is accessed via
    a `CCM::Configuration` instance (in particular, when a call to `_prepareElement`
    is made).
    As a consequence, an unlocked Configuration instance will always use the
    CacheManager's current CID.

    Unless the anonymous flag is set to true, each process that creates a
    Configuration instance, creates a file named `ccm-active-profile.$cid.$pid`
    (with `$cid` the CID and `$pid` the process ID) under the `profile.$cid`
    directory in the `CacheManager` cache path. The presence of this file protects
    the process from getting this particular CID removed by the `ccm-purge` command
    (e.g. by the daily purge cron job).
    If the anonymous flag is set to -1, the permissions of the user to create this file
    are verified, and if the user can write to this file, the anonymous flag is set to
    false (this is only verified once during initialisation).

    Processes that have no permission to create this file (or don't care about long
    runtimes), can set the `anonymous` flag and use the configuration
    (at their own risk).

- getConfigurationId ()

    Returns configuration id.

- lock ()

    Lock configuration (local lock).

- unlock ()

    Unlock configuration (local unlock).

- isLocked ()

    Returns true if the configuration is locked, otherwise false

- getName

    Return the name of the Configuration
    based on the name template set during initialisation.

    The `type` argument (default `name`) specifies which
    name format is used.
    The actual template used is `` CCM/names/<name_template>/`type`.tt ``.

    Following types are defined

    - name: (compact) name

    The data used for rendering is the `/metadata` tree.

    The rendered text is stripped from any leading and/or trailing whitespace
    and is added to the `name` attribute,
    the next `getName` call will return the cached value.

    If no template was set, undef is returned.
    If there was rendering (or any other) failure,
    undef is returned and the fail attribute is set.

- getElement ($path)

    Returns Element object identified by $path (path may be a string or
    and object of class Path)

- getValue ($path)

    returns value of the element identified by $path

- elementExists ($path)

    returns true if elements identified by $path exists

- getTree ($path)

    returns `getTree` of the element identified by `$path`.
    Any other optional arguments are passed to `getTree`.

    If the path does not exist, undef is returned. (Any error
    reason is set as the `fail` attribute and the error is ignored.)
