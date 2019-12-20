
#####################################
NCM\::Component\::OpenStack\::Service
#####################################


Functions
=========



- get_flavour
 
 Determine the name of the flavour based on type and tree and log/reporter instance
 (eg name=keystone for type=identity)
 


- get_fqdn
 
 Get ``fqdn`` of the host using host profile ``config`` instance.
 


- get_service
 
 Service factory: loads custom subclasses when one exists
 Same args as _initialize
 


- run_service
 
 Convenience function around get_service, includes basic reporting
 



Methods
=======



- _init_attrs
 
 Arguments:
 
 
 - type: eg identity
 
 
 
 - config: full profile config instance
 
 
 
 - log: reporter instance
 
 
 
 - prefix: the component prefix (for subclassing)
 
 
 
 - client: Net::OpenStack::Client instance
 
 
 


- _initialize
 
 Initialisation using ``_init_attrs``, ``_attrs`` and ``_daemons``.
 


- _daemons
 
 Method to customise the ``daemons`` attribute during ``_initialize``.
 


- _set_elpath
 
 Return main element path
 


- _attrs
 
 Add/set/modify more attributes
 Convenience method for inheritance
 instead of using SUPER
 
 
 .. code-block:: perl
 
      my $res = $self->SUPER::method(@_);
 
 


- _get_json_tree
 
 Return the getTree result on ``path``, in JSON data format.
 (Relative paths are relative to the prefix).
 


- _render
 
 Returns CCM::TextRedner instance
 


- _file_opts
 
 Return hashref with filewriter options for ``service``
 (incl owned by that service user)
 


- _write_config_file
 
 Write the config file with name ``filename`` and ``element`` instance.
 


- _write_config_files
 
 Write multiple config files based on entries in the ``tree`` attribute.
 Filename is based on mapping in the ``filename`` attribute;
 a mapping which daemon(s) to start when the file is modified can
 be provided via the ``daemon_map`` attribute.
 


- write_config_file
 
 Write the config files (when ``filenames`` attribute is a hashref) or single file otherwise.
 


- _read_ceph_keyring
 
 Read Ceph pool key file from ``keyring``.
 


- _libvirt_ceph_secret
 
 Set the libvirt ``secret`` file and
 couple the ``uuid`` to the Ceph key from the ``keyring``.
 


- _do
 
 Convenience wrapper around CAF::Process
 
 Options
 
 
 - user: option passed to ``CAF::Process``
 
 
 
 - sensitive: option passed to ``CAF::Process``
 
 
 
 - test: the command is a test, no error will be reported on failure
 
 
 


- pre_populate_service_database
 
 Run before the default service database is poulated
 (it is not run when database was already present).
 
 Must return 1 on success;
 


- populate_service_database
 
 Run the database sync command (incl bootstrap when empty)
 if db version cannot be found.
 
 Must return 1 on success.
 


- post_populate_service_database
 
 Run after the service database is poulated
 (it is not run when database was already present).
 
 Must return 1 on success;
 


- restart_daemons
 
 Restarts system service(s) after any configuration
 change for OpenStack ``service`` service.
 


- pre_restart
 
 Run before possible restart of services
 Must return 1 on success
 


- run_client
 
 Configure the service (typically using REST client).
 Must return 1 on success.
 


- run
 
 Do things (in following order):
 
 
 - flavour configuration
  
  
  - write_config_file
  
  
  
  - populate_service_database (or return)
  
  
  
  - pre_restart (or return)
  
  
  
  - restart_daemons (if config file changed)
  
  
  
 
 
 - service configuration
  
  
  - run_client
  
  
  
 
 


