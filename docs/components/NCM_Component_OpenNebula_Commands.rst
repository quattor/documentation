
#######################################
NCM\::Component\::OpenNebula\::Commands
#######################################


****
NAME
****


``NCM::Component::OpenNebula::Commands`` Configuration module for ONE


***********
DESCRIPTION
***********


Configuration module for OpenNebula. Executes the required ssh commands
to enable the hosts to be used by the cloud server.

This component needs a 'oneadmin' user.
The user should be able to run these commands with sudo without password:


- ``virsh secret-define --file `/var/lib/one/templates/secret/secret_ceph.xml```



- ``virsh secret-set-value --secret $uuid --base64 $secret``



Public methods
==============



- set_ssh_command
 
 Sets ``$sshcmd``.
 


- run_command
 
 Executes a command and return the output.
 Returns sdout and stderr array.
 


- run_virsh_as_oneadmin_with_ssh
 
 Executes a command prefixed with ``virsh`` and returns the output.
 


- run_oneuser_as_oneadmin_with_ssh
 
 Executes ``oneuser`` command and returns the output.
 


- run_onehost_as_oneadmin_with_ssh
 
 Executes ``onehost`` command to sync hosts VMMs scripts.
 


- has_shell_escapes
 
 Checks for shell escapes.
 


- run_command_as_oneadmin
 
 Executes a command as ``oneadmin`` user.
 


- run_command_as_oneadmin_with_ssh
 
 Executes a command as ``oneadmin`` over ssh, optionally with options.
 


- ssh_known_keys
 
 Accepts and adds unknown keys if wanted.
 


- can_connect_to_host
 
 Checks if the host is reachable or not.
 



