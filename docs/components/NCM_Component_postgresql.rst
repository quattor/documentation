
############################
NCM\::Component\::postgresql
############################


****
NAME
****


postgresql : NCM component to manage PostgreSQL configuration.


***********
DESCRIPTION
***********


This component allows to manage configuration of PostgreSQL.
It's very basic in functionality (originally developed for dcache usage).


***********
DESCRIPTION
***********


The component to configure postgresql databases


**************
public methods
**************



- create_postgresql_config
 
 Create main or hba config via textrender. Returns undef on failure, changed state otherwise.
 The ``data`` hash is either ``%MAIN_CONFIG`` or ``%HBA_CONFIG``;
 or the pg_alter hashref (see ``pg_alter`` method).
 


- fetch
 
 Get ``$path`` from ``$config``, if it does not exists, return ``$default``.
 If ``$default`` is not defined, use empty string as default.
 
 If ``$path`` is a relative path, it is assumed relative from ``$self->prefix``.
 


- get_version
 
 Return version instance ``v$major.$minor.$remainder`` version information (from ``postmaster --version``)
 
 Return undef in case of problem.
 


- initdb
 
 Initialise the database. End result is a stopped initialised database.
 
 Returns undef on failure.
 


- prepare_service
 
 Perform installation sanity check, and generates the
 pgsql sysconfig entry.
 
 Returns undef on failure, the changed state of the pgsql
 sysconfig file otherwise
 


- whoami
 
 Return a hashref with configuration related data to indentify
 the service to use
 
 
 - service
  
  Service instance to use
  
 
 
 - version
  
  Return value from ``version`` method
  
 
 
 - pg
  
  A hashref with postgresql basic configuration data,
  required to start the database.
  
  
  - dir
   
   The database base directory
   
  
  
  - data
   
   The database 'data' subdirectory
   
  
  
  - port
   
   The database port
   
  
  
  - log
   
   The database startup log
   
  
  
  - engine
   
   Location of service binaries
   
  
  
 
 
 - suffix
  
  Version related suffix (or empty string if none is required).
  E.g. '-9.2', part of e.g. default servicename, pg_engine, ...
  
 
 
 - exesuffix
  
  Version related suffix for certain executables, like '92' in
  'postgresql92-setup'.
  
 
 
 - defaultname
  
  The default service name
  
 
 
 - servicename
  
  The actual servicename
  
 
 
 - service
  
  The ``NCM::Component::Postgresql::Service`` instance
  
 
 
 - commands
  
  The ``NCM::Component::Postgresql::Commands`` instance
  
 
 
 Return hashref or undef on failure. No errors are logged
 


- sanity_check
 
 Run some additional sanity checks, return undef on failure.
 


- recovery_configuration
 
 Handle recovery file creation
 
 Returns undef on failure, changed recovery state otherwise.
 


- start_postgres
 
 Try to start postgres service, the cautious way.
 
 Return undef on failure, SUCCESS otherwise.
 


- pg_alter
 
 Process roles and databases. Returns undef on failure.
 
 The main purpose is to initialise postgresql.
 


- roles
 
 ``$roles_tree`` is the roles configuration hashref (via ``config->getTree(prefix/roles)``).
 
 Roles and only added and modified, never removed.
 
 Return undef on failure.
 


- databases
 
 ``$dbs_tree`` is the databases configuration hashref (via ``config->getTree(prefix/databases)``).
 
 Databases are only created, never modified or removed.
 
 Return undef on failure.
 
 Operation order is
 
 
 - create database
 
 
 
 - initialise with installfile
 
 
 
 - create lang
 
 
 
 - apply langfile (if lang defined)
 
 
 


- Configure
 
 component Configure method
 


