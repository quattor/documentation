######################
functions\::validation
######################

Types
-----

 - **valid_user**
    - Description: This type is meant to be used to check if strings provided are valid user names. This is however designed to be overriden by site-specific policies. The regex used here as default is the one suggested by the useradd man page.

Variables
---------

 - VALID_USER_PATTERN

Functions
---------

 - is_component_list
    - Description: checks that the argument is a list and that all the strings identify existing components
    - Arguments:
        - list of valid components
 - check_mount
    - Description: adds the mountpoint entry of a given resource to the mount table, if it does not exist there so far, else drops an error
 - is_profile_list
    - Description: checks that the argument is a list and that all its elements identify existing profiles. Each name in profiles will be matched against 'foo' and 'profile_foo', which are considered to be the same, but the latter form is forbidden in the input list.
 - is_a_fcahwaddr
    - Description: checks if the argument is a fiber-channel-style hardware address
 - is_card_port
    - Description: returns true if the argument is a defined card port
 - is_valid_card_ports
    - Description: returns true if all the controller and port indexes are numeric (but have a leading _ to make them work as nlists).
 - valid_absolute_file_paths
    - Description: Checks keys of a dict are valid absolute paths to files (not directories) using is_absolute_file_path
