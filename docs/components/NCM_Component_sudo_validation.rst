###################################
NCM\::Component\::sudo - validation
###################################

Functions
---------

 - sudo_check_aliases_list
 - sudo_check_default_options_list
    - Description: Checks the validity of the default options. This means that AT MOST one of "user", "run_as" or "host" may be specified on each entry.
 - sudo_is_structure_component
    - Description: Sanity checks for SUDO component. A privilege line with any field in capitals will be checked against aliases for its existence.
