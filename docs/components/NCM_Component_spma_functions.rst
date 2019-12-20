##################################
NCM\::Component\::spma - functions
##################################

Functions
---------

 - repository_exists
    - Description: Utility function to determine if at least one particular child element exists. (Used in the checking of the repositories.)
    - Arguments:
        - name
        - path to list of dicts with at least one key 'name'
 - resolve_pkg_rep
    - Description: Automatically fill "repository" field for package list
    - Arguments:
        - repository list
        - (optional) package list. When specified, only the package(s) specified are resolved, if they exist in the configuration.
 - purge_rep_list
    - Description: Remove unneeded repository information
    - Arguments:
        - repository list
 - pkg_del
    - Description: Remove package from list. If the package is not part of the configuration, silently exit: this is not considered as an error.
    - Arguments:
        - name
        - (optional) version. If version is not specified (no argument provided) or is the empty string then ALL existing versions are removed from the profile.
        - (optional) arch. If arch is not specified (no argument provided), then ALL existing archs for the specified version are removed from the profile.
 - pkg_repl
    - Arguments:
        - name
        - (optional) new version
        - (optional) arch
        - (optional) options. pkg_repl() is the real workhorse of pkg_add/pkg_del/pkg_repl/pkg_ronly. Other functions are just wrappers of pkg_repl(). 'options' argument is used to tailor this function behaviour for a particular purpose and is normally used only by other pkg_xxx functions.
 - pkg_add
    - Arguments:
        - name
        - (optional) version
        - (optional) arch
 - pkg_ronly
    - Description: Replace package in the list ONLY if present. Same as pkg_repl() except that if no version existed in the profile, NO new version is added. See pkg_repl() for argument documentation.
    - Arguments:
        - name
        - (optional) version
        - (optional) arch
