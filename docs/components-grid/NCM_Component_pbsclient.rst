
###########################
NCM\::Component\::pbsclient
###########################


****
NAME
****


NCM::pbsclient - NCM pbsclient configuration component


********
SYNOPSIS
********



- Configure()
 
 Do the necessary configuration for an PBS client at CERN. The mail two configuration files
 are `/var/spool/pbs/mom_priv/config` and `/var/spool/pbs/server_name.` The first one is the 
 default configuration file for PBS, the second one is used to hold the PBS server name.
 In case Torque behaviour is selected, the server_name is contained in the config file
 as well.
 


- Unconfigure()
 
 Removed the configuration file for pbs mom (but leaves the pbs server_name file).
 



*********
RESOURCES
*********



- `/software/components/pbsclient/active` : boolean
 
 activates/deactivates the component.
 


- `/software/components/pbsclient/cpuinfo` : string[]
 
 Defines which cpu info (from `/proc/cpuinfo`) to define as resources in the pbs_mom config file.
 This is a string list, which may contain any processor property name that you can see in
 `/proc/cpuinfo` file.
 Two extra processor related flags can be specified : ncpus, and ncores
 ncpus is the number of physical CPUs in the node, and ncores is the total number of cores.
 \*\* All CPUs in one host are assumed to be the same \*\*
 
 Example properties are : "ncores", "ncpus", "flags", "model name", "cpu MHz", "cpu family", "model", "stepping"
 
 Properties that start with "model " or "cpu " will see this be stripped as a first step.
 All resulting pbs_mom resources will be prefixed with ``cpu_`` except ncpus and ncores.
 


- `/software/components/pbsclient/masters` : string[]
 
 defines a list of PBS masters for this host. The first is the primary master
 for q\* commands. This directive is compulsory.
 


- `/software/components/pbsclient/resources` : string
 
 defines the PBS resources, this host provides.  This resource is currently ignored.
 


- `/software/components/pbsclient/restricted` : string[]
 
 defines the list of hosts that can query PBS mom for additional information using
 a reserved port (in addition to the clienthosts as set fia the masters resource).
 


- `/software/components/pbsclient/logEvent` : long
 
 Bitmask defining what log information to write to the mom_log files.
 


- `/software/components/pbsclient/tmpdir` : string
 
 Location of the per-job transient TMPDIR directory. This resource is only
 functional on OpenPBS or Torque servers with the transient_tmpdir patch
 applied. The default is compiled into mom.
 


- `/software/components/pbsclient/idealLoad` : double
 
 Translates into configuration directive $idealload.
 


- `/software/components/pbsclient/maxLoad` : double
 
 Translates into configuration directive $maxload.
 


- `/software/components/pbsclient/cpuTimeMultFactor` : double
 
 Translates into configuration directive $cput.
 


- `/software/components/pbsclient/wallTimeMultFactor` : double
 
 Translates into configuration directive $wallt.
 


- `/software/components/pbsclient/prologAlarmSec` : long
 
 Translates into configuration directive $prologalarm.
 


- `/software/components/pbsclient/checkpoint_interval` : long



- `/software/components/pbsclient/checkpoint_script` : string



- `/software/components/pbsclient/restart_script` : string



- `/software/components/pbsclient/checkpoint_run_exe` : string



- `/software/components/pbsclient/configPath` : string
 
 location of the PBS mom configuration file (default: 
 ``/var/spool/pbs/mom_priv/config``).  Note that the server_name file is 
 written two directories up (thus by default in ``/var/spool/pbs``).
 


- `/software/components/pbsclient/behaviour` : string
 
 The way the server_name is conveyed to PBS mom. The default is
 OpenPBS, where the name is written to the file "server_name". The
 only other valid value is "Torque", where the name is written
 in the "$pbsservername" directive in the mom config file.
 


- `/software/components/pbsclient/nodeCheckScriptPath` : string



- `/software/components/pbsclient/nodeCheckIntervalSec` : long



- `/software/components/pbsclient/initScriptPath` : string
 
 Name of the init.d script to run in the configuration changed. BY
 default this is "``/etc/init.d/pbs``".
 


- `/software/components/pbsclient/directPaths` : component_pbsclient_pathmapping_type[]
 
 Locations that are accesible directly using the POSIX FileIO calls (i.e. without
 using pbs_rcp). This array of records define dthe list of $usecp directives.
 The component_pbsclient_pathmapping_type contains two resources ("locations" and "path").
 


- `/software/components/pbsclient/scripts/prologue` : string =item `/software/components/pbsclient/scripts/epilogue` : string =item `/software/components/pbsclient/scripts/prologue.user` : string =item `/software/components/pbsclient/scripts/epilogue.user` : string =item `/software/components/pbsclient/scripts/prologue.parallel` : string
 
 These scripts may be defined to augment the behavior of pbs when
 starting and ending jobs.  See the pbs documentation for a complete
 description of when each script runs and as what user.
 


- `/software/components/pbsclient/submitonly` ? boolean
 
 If true, it assumes this host is only used for job submission, and has no pbs MOM running
  that requires restarting.
 