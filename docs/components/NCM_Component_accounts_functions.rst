######################################
NCM\::Component\::accounts - functions
######################################

Types
-----

 - **/software/components/accounts/defined_user**
 - **/software/components/accounts/defined_group**

Variables
---------

 - ACCOUNTS_USER_HOME_ROOT
 - ACCOUNTS_USER_CREATE_HOME
 - ACCOUNTS_USER_AUTOGROUP
 - ACCOUNTS_USER_CHECK_GROUP
 - ACCOUNTS_IGNORE_MISSING_GROUPS
 - ACCOUNTS_USER_COMMENT
 - ACCOUNTS_GROUP_COMMENT

Functions
---------

 - is_user_or_group
    - Arguments:
        - the type ('user' or 'group')
        - the name(s). Can be more than one argument or a single list of names. All arguments have to be defined.
 - create_group
 - create_user
 - create_accounts_from_db
 - keep_user_group
