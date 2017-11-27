
### NAME

NCM::Component::spma::yum - NCM SPMA configuration component for Yum

### SYNOPSIS

This document describes how to control the behaviour of the package
manager itself. For information on how to manage packages with
Quattor, please check
[http://quattor.org/documentation/2013/04/05/package-management.html](http://quattor.org/documentation/2013/04/05/package-management.html).

### RESOURCES

- `/software/components/spma/active` : boolean

    Activates/deactivates the component.

#### Flags for Yum processing:

- `/software/components/spma/process_obsoletes` : boolean

    Make Yum replace obsoleted packages by their recommended counterparts.
    Defaults to `false` to keep backwards compatibility.

- `/software/components/spma/userpkgs` : string ("yes|no")

    Whether SPMA should keep any packages the user may have installed
    manually.

    Set to `no` to make the SPMA take full control of all your software
    installations. Set to `yes` to preserve any packages you installed
    by hand. If you do so, SPMA will never remove a package.

- `/software/components/spma/userpkgs_retry` : boolean

    Yum-based spma might get confused and fails when it tries
    to remove packages when `userpkgs` is `no` while installing
    new ones. Typically it will (try to) remove a
    leaf package, that is also to be installed as a dependency of a new
    to-be-installed package.

    With `userpkgs_retry` set to `true`, the package update process
    will be retried in case of failure in 2 steps, a first retry while
    preserving the installed packages, and if this retry was succesful,
    followed by a second retry where it will (try to) remove leaf packages
    again.

- `/software/components/spma/packager` : string

    Must contain `yum` to use this module.

- `/software/components/spma/proxy` : string ("yes|no")

    Whether to use a proxy.

- `/software/components/spma/proxytype` : string ("forward|reverse")

    Type of proxy (reverse or forward).

- `/software/components/spma/proxyhost` : string

    Comma-separated list of proxy hosts. If you have a forward proxy you
    should specify only one. You may specify several reverse proxies
    here, and they will be appended to the `baseurl` entry of each
    repository's configuration.

- `/software/components/spma/proxyport` : string

    Port where the proxies are listening.

- `/software/components/spma/run` : string ("yes|no")

    Whether to actually run Yum operations that may install, remove or
    update packages.

- `/software/components/spma/fullsearch` : boolean

    Yum-based spma will try to verify that all version locked packages
    can actually be found in the provided repositories. For packages
    that have versions with wildcards specified, a full (and possibly slow)
    search of each pattern can be performed by setting `fullsearch` to true.
    By default, the fullsearch is not performed, and for any packages that have
    versions with wildcards, it is assumed that the repositories contain them.

### FILES

- `/etc/spma.conf`
- `/var/lib/spma-target.cf`

### NOTES

This component honors the `--noaction` mode.

### SEE ALSO

You must read this document to understand how to manage packages
with Quattor:

[http://quattor.org/documentation/2013/04/05/package-management.html](http://quattor.org/documentation/2013/04/05/package-management.html),

These links detail experiences and strategies relevant for managing
software installations in large sites:

- [http://quattor.org/documentation/2013/02/07/yum-package-management.html](http://quattor.org/documentation/2013/02/07/yum-package-management.html)
- [http://quattor.org/documentation/2013/01/29/spma-yum-upgrade.html](http://quattor.org/documentation/2013/01/29/spma-yum-upgrade.html)
- [http://quattor.org/blog/2013/01/29/package-layout-proposal.html](http://quattor.org/blog/2013/01/29/package-layout-proposal.html)
- [http://quattor.org/blog/2013/03/27/cleaning-up-packages.html](http://quattor.org/blog/2013/03/27/cleaning-up-packages.html)
