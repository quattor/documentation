
#####################################
NCM\::Component\::OpenNebula\::Server
#####################################


****
NAME
****


``NCM::Component::OpenNebula::Server`` adds ``OpenNebula`` service configuration
support to ``NCM::Component::OpenNebula``.

Public methods
==============



- restart_opennebula_service
 
 Restarts ``OpenNebula`` service after any configuration change.
 


- detect_opennebula_version
 
 Detects ``OpenNebula`` version through opennebula-server probe files,
 the value gathered from the file must be untaint.
 


- change_opennebula_passwd
 
 Sets a new ``OpenNebula`` service password.
 


- set_one_service_conf
 
 Sets ``OpenNebula`` configuration files used by
 the deamons, if the configuration file is changed the
 service must be restarted afterwards.
 


- is_conf_file_modified
 
 Checks ``OpenNebula`` configuration file status.
 


- set_one_auth_file
 
 Sets the authentication files used by
 ``oneadmin`` client tools.
 


- set_file_opts
 
 Sets filewriter options.
 


- set_one_server
 
 Configures ``OpenNebula`` server.
 


- set_config_group
 
 Sets ``OpenNebula`` configuration file group.
 



