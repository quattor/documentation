
###########################
NCM\::Component\::fmonagent
###########################


****
NAME
****


NCM::fmonagent - NCM Lemon Monitoring Agent configuration component


********
SYNOPSIS
********



- Configure()
 
 Creates configuration file(s) and restarts the lemon-agent service.
 In case of the single file configuration the files
 is defined in the CDB template as file and in case of split file as 
 a directory where the following structure is expected:
 
 
 .. code-block:: perl
 
  	top_dir/general.conf
  	top_dir/transport/
  	top_dir/metrics/
  	top_dir/sensors/
 
 
 Component will try in this case to modify the ``top_dir/general.conf``,
 ``top_dir/transport/udp.conf``, ``top_dir/metrics/default.conf`` and
 for each sensor ``top_dir/sensors/sensor_name.conf`` files.
 



*********
RESOURCES
*********



- ``/software/components/fmonagent/active`` : boolean
 
 Activates/deactivates the component.
 


Warning
=======


This version of NCM::fmonagent will not work with sensorAlarm!


Required programs.
==================


Requires lemon-agent rpm to be installed.


