
#######
ncm-ncd
#######


****
NAME
****


ncm-ncd - Node Configuration Dispatcher

Part of the NCM (Node Configuration Management) subsystem

quattor toolsuite http://quattor.org


********
SYNOPSIS
********



.. code-block:: perl

     ncm-ncd --configure   [options] [<component1> [<component2>] ...]
     ncm-ncd --unconfigure [options] component


(See ``ncm-ncd --help`` for full list of options with default values.)


***********
DESCRIPTION
***********


The \ **ncm-ncd**\  is the front end for invoking NCM configuration
components. The \ **ncm-ncd**\  is called with a list of components to be
invoked as an argument. Based on this list, the \ **ncd**\  looks up the
inter-component dependencies, orders the components, and invokes each
component sequentially.

If no component is specified, the \ **ncd**\  will invoke all
components which are marked as active in the node configuration
profile. These are considered to be the 'default' components to run.

The \ **ncd**\  can be executed manually, via \ **cron**\ , or via the
\ **cdispd**\ .

If a dependency is not fulfilled, the \ **ncd**\  exits with an
appropriate error message and return status.

In case of deinstallation of a component using ``--unconfigure``,
the \ **ncd**\  is to be called with the component's name as a
parameter.


*******
OPTIONS
*******



- --list
 
 Does nothing but list all found components, in the following format:
 
 name - active? - installed?
 


- --configure
 
 Run the ``Configure`` method for <component1 component2 ...> (default option).
 For running configure on all components, use --configure --all.
 


- --all
 
 See above. Run --configure --all to run configure on all components.
 


- --skip <component>
 
 Skip one component (only to be used with --all)
 


- --unconfigure
 
 Run the ``Unconfigure`` method for <component>. Only one component can
 be unconfigured at a time.
 


- --logdir <dir>
 
 Directory where to place ncm-ncd and component log files
 


- --log_group_readable <groupname>
 
 Group readable logdir (value is the groupname).
 If set with valid groupname, the configured logdirectory
 will have its permissions set to 750 and the
 the groupname as group (still owned by root).
 
 Following standard UNIX ACL semantics, the ``log_group_readable`` configuration
 option is not very useful if ``log_world_readable`` is also true.
 


- --log_world_readable <0|1>
 
 World readable logdir flag (1/0). If true, the configured logdirectory
 will have its permissions set to 755. If false (the default) the permissions will be 700.
 
 These permissions will be set each time ``ncm-ncd`` is run.
 
 Following standard UNIX ACL semantics, the ``log_group_readable`` configuration
 option is not very useful if ``log_world_readable`` is also true.
 
 The use of ``log_world_readable`` is not recommended
 if profiles contain sensitive or private information.
 


- --logpid
 
 Add process ID to the log messages (disabled by default).
 


- --verbose_logfile <0|1>
 
 Report with verbose loglevel to the logfile (default enabled)
 


- --retries <n>
 
 Try 'n' times if locked (another ncm-ncd instance is running).
 


- --state <dir>
 
 Directory in which to find state files. On conclusion of any component
 configuration, if the configuration was successful then the component
 file will be deleted from this state directory. If a component
 produces errors, then the component file will contain the number of errors.
 In other words, if a configuration is clean then there will be
 no files within the state directory. If there are any problems with
 the configuration, then there will be a file for the failing
 components. An empty file indicates that the component has not
 completed its configuration. If this option is not defined, then
 no state files will be maintained.
 


- --timeout <n>
 
 Wait a maximum of 'n' seconds between retries.
 


- --useprofile <profile_id>
 
 Use <profile_id> as NVA-API configuration profile ID (default: latest)
 


- --cache_root <directory>
 
 CCM cache root directory (optional, otherwise CCM default taken)
 


- --multilog
 
 Use separate (per component) log files in log directory
 


- --pre-hook
 
 Hook to be executed before any component is run.  It receives a JSON
 object with the list of components that will be executed.
 
 To see the exact form of the input run
 
 
 .. code-block:: perl
 
      ncm-ncd --configure <some-comp> --pre-hook `/bin/cat`
 
 


- --post-hook
 
 Hook to be executed after all components have run.  It receives a JSON
 object via stdin with the components that succeeded, failed or had
 warnings.
 


- --pre-hook-timeout, --post-hook-timeout
 
 Timeouts, in seconds, for the ``--pre-hook`` and ``--post-hook``
 
 A value of 0 means no time out.  By default they time out after 5 minutes.
 


- --chroot
 
 Chroot to the directory given as an argument.  If it's not possible to
 chroot, ``ncm-ncd`` will die.
 


- --check-noquattor
 
 Check if CCM updates are disabled globally via the `/etc/noquattor` file.
 And do not run if CCM updates are globally disabled.
 (If --check-noquattor is not set, ncm-ncd will ignore `/etc/noquattor`).
 
 It is enabled by default, use ``--no-check-noquattor`` to disable it
 (or set ``check-noquattor = 0`` in the configfile).
 


- --history
 
 Enable history/event tracking. (Enabled by default).
 


- --force-quattor
 
 Run even if CCM updates are globally disabled (and --check-noquattor is set).
 


Advanced Options
================


Following options are advanced options (typically used for debugging and/or testing).
Use with care.


- --ignorelock
 
 Ignore existing application lock. Use with care.
 


- --forcelock
 
 Take over application lock. Use with care.
 


- --nodeps
 
 ignore broken dependencies when invoking configure. Use with care.
 
 missing pre/post dependencies are ignored during resolution;
 and during the ordered execution of all components, failing
 predependencies are not considered broken and allow the execution
 of the component.
 


- --ignore-errors-from-dependencies
 
 errors from dependencies are downgraded to warnings, to make the
 overall ncm-ncd run pass if a dependency fails. This option implies
 '--nodeps' and '--autodeps'. Use with care.
 
 A "dependency" is any component that is not requested/specified
 via command line (and added to list of components to process via
 '--autodeps', if any).
 
 (If you do not care about dependencies and just want to avoid errors,
 you can also try to use '--nodeps --no-autodeps').
 


- --autodeps
 
 Expand missing pre/post dependencies in configure (default to true).
 (Disable with --no-autodeps. Use --no-autodeps with care.)
 


- --allowbrokencomps
 
 Do not stop overall execution if 'broken' components are found, just ignore
 these ('broken' components: component file missing or not instantiable). Use with care.
 


- --history-instances
 
 Enable history/event instances tracking. Use with care.
 



Other Options
=============



- --help
 
 Displays a help message with all options and default settings.
 


- --version
 
 Displays application version information.
 


- --verbose
 
 Print verbose details on operations.
 


- --debug <1..5>
 
 Set the debugging level to <1..5>.
 


- --facility <f>
 
 Set the syslog facility to <f> (Eg. local1).
 


- --quiet
 
 Suppress application output to standard output.
 


- --noaction
 
 Do not actually perform operations.
 


- --include <directories>
 
 A colon-seperated list of directories to include in search path for ncm-components
 




******************
CONFIGURATION FILE
******************


A configuration file can keep site-wide configuration settings. The
location of the configuration file is defined in the ``--cfgfile``
option. A default configuration file is found in
``/etc/ncm-ncd.conf``.


***************
SIGNAL HANDLING
***************


If a signal is received, the ncm-ncd will try to finish its execution
gracefully and will report an error (return status: -1), except if
it was called with the ``--noaction`` flag.

