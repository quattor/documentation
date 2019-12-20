################################
NCM\::Component\::mysql - schema
################################

Types
-----

 - **/software/components/mysql/component_mysql_user_right**
 - **/software/components/mysql/component_mysql_db_user**
    - */software/components/mysql/component_mysql_db_user/password*
        - Required
        - Type: string
    - */software/components/mysql/component_mysql_db_user/rights*
        - Required
        - Type: component_mysql_user_right
    - */software/components/mysql/component_mysql_db_user/shortPwd*
        - Required
        - Type: boolean
        - Default value: false
 - **/software/components/mysql/component_mysql_db_script**
    - */software/components/mysql/component_mysql_db_script/file*
        - Optional
        - Type: string
    - */software/components/mysql/component_mysql_db_script/content*
        - Optional
        - Type: string
 - **/software/components/mysql/component_mysql_db_options**
    - */software/components/mysql/component_mysql_db_options/server*
        - Required
        - Type: string
    - */software/components/mysql/component_mysql_db_options/users*
        - Optional
        - Type: component_mysql_db_user
    - */software/components/mysql/component_mysql_db_options/initScript*
        - Optional
        - Type: component_mysql_db_script
    - */software/components/mysql/component_mysql_db_options/initOnce*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/mysql/component_mysql_db_options/createDb*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/mysql/component_mysql_db_options/tableOptions*
        - Optional
        - Type: string
 - **/software/components/mysql/component_mysql_server_options**
    - */software/components/mysql/component_mysql_server_options/host*
        - Optional
        - Type: string
    - */software/components/mysql/component_mysql_server_options/adminuser*
        - Required
        - Type: string
    - */software/components/mysql/component_mysql_server_options/adminpwd*
        - Required
        - Type: string
    - */software/components/mysql/component_mysql_server_options/options*
        - Optional
        - Type: string
    - */software/components/mysql/component_mysql_server_options/users*
        - Optional
        - Type: component_mysql_db_user
 - **/software/components/mysql/component_mysql**
    - */software/components/mysql/component_mysql/databases*
        - Optional
        - Type: component_mysql_db_options
    - */software/components/mysql/component_mysql/servers*
        - Required
        - Type: component_mysql_server_options
    - */software/components/mysql/component_mysql/serviceName*
        - Required
        - Type: string
        - Default value: mysqld

Functions
---------

 - component_mysql_valid
 - component_mysql_check_db_script
 - component_mysql_password_valid
