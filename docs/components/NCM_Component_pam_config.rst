##############################
NCM\::Component\::pam - config
##############################

Functions
---------

 - pam_add
    - Description: add a line to pam configuration
    - Arguments:
        - service
        - pamtype
        - control
        - module
        - options, can be hash or list
 - pam_add_stack
 - pam_add_listfile_acl
 - pam_add_access_file
 - pam_add_access_lastacl
 - pam_add_access_acl
 - pam_add_access_netgroup
 - pam_add_access_group
    - Description: helper function to add (unix) group to pam/access/<key>
    - Arguments:
        - key under components/pam/access to modify
        - group, unix group to add to <key>
 - pam_add_access_user
