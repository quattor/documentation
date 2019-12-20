
##########################
NCM\::Component\::wlconfig
##########################


****
NAME
****


ncm-wlconfig: NCM wlconfig component


***********
DESCRIPTION
***********


The \ *ncm-wlconfig*\  component manages the configuration files of the WP1
NetworkServer, LogMonitor, JobController, and WorkloadManager
services.  All of these services read the `/opt/edg/etc/edg_wl.conf`
file.


*********
RESOURCES
*********


configFile (edg_wl.conf)
========================


The name of the configuration file.  It will be created in the
location EDG_LOCATION/etc.


user (edguser)
==============


The username to use to run the services.


grisCache (1)
=============


If set to "1" it enables the UseCacheInsteadOfGris flag.  This is used
by the NetworkServer and the WorkloadManager.


jobController
=============


condorSubmit ()
---------------


The absolute filename of the condor_submit executable.


condorRemove ()
---------------


The absolute filename of the condor_rm executable.


condorQuery ()
--------------


The absolute filename of the condor_q executable.


condorSubmitDAG ()
------------------


The absolute filename of the condor_submit_dag executable.


condorRelease ()
----------------


The absolute filename of the condor_release executable.


submitFile
----------


The directory where the temporary files are created (CondorG submit
file and job wrapper scripts).


outputFile
----------


The directory where the standard output and error streams of CondorG
are cached.


queueFile
---------


The JobController input queue of requests.


log/file
--------


The absolute file name of the JobController log file.


log/level (5)
-------------


The level for the logging.


container (1000)
----------------


The number of jobs after which the JobController must re-read the
IdRepositoryName LogMonitor file.



LogMonitor
==========


jobsPerCondorLog (1000)
-----------------------


The number of jobs whose events are recorded for each single CondorG
log file.  I.e. every jobsPerCondorLog jobs, the log file is changed.


mainLoopDuration (10)
---------------------


It defines how often the LogMonitor reads the CondorG log file.
I.e. every mainLoopDuration seconds the LogMonitor reads these files.


condorLogDir
------------


The directory where the CondorG log file are created.


condorRecycleDir
----------------


The directory where the CondorG log files which have already been read
are stored.


internalMonitorDir
------------------


The directory where some files needed by the LogMonitor service are
created and stored.


idRepositoryName (irepository.dat)
----------------------------------


The name of the file used by the LogMonitor for internal purposes (the
storage of the jobID/CondorID correspondance).


abortedJobsTimeout (600)
------------------------


The timeout (in seconds) to have a cancelled job forgotten by the
LogMonitor (useful when the job hangs in the CondorG queue).


log/file
--------


The absolute file name of the JobController log file.


log/level (5)
-------------


The level for the logging.



NetworkServer
=============


iiHost, iiPort, iiDN, iiTimeout
-------------------------------


The contact parameters for the II.  The host must be defined by the
user.  The default values are 2135, "mds-vo-name=local, o=grid", and
30 for the iiPort, iiDN, and iiTimeout parameters, respectively.


grisPort, grisDN, grisTimeout
-----------------------------


The contact parameters for the GRISes.  The default values are 2135,
"mds-vo-name=local, o=grid", and 20 for the grisPort, grisDN, and
grisTimeout parameters, respectively.


listeningPort (7772)
--------------------


The port used by the NetworkServer to receive requests.


masterThreads (8)
-----------------


The maximum number of simultaneous connections with UserInterfaces.


dispatcherThreads (8)
---------------------


The maximum number of simultaneous connections (to forward the
incoming requests) with the WorkloadManager.


sandboxStagingPath
------------------


The absolute pathname of the sandbox staging directory.  It is also
the location where the .BrokerInfo file is stored.


quotaManagement
---------------


Boolean indicating whether the system should check file quotas for the
input sandboxes.


quotaManagement, quotaSandboxSize
---------------------------------


The quotaManagement flag is a boolean indicating whether or not the
quotas should be checked for the input sandboxes.  The
quotaSandboxSize is the maximum size of a single input sandbox.


quotaAdjustment, quotaAdjustmentAmount
--------------------------------------


The quotaAdjustment is a boolean indicating whether or not dynamic
quotas should be used (i.e. the system administrator has not set a
system quota).  The adjustment amount is the value by which the
dynamic quota is increased/decreased as jobs enter and leave the
system.


reservedDiskPercentage (2.0)
----------------------------


Is a double representing the percentage of the disk (storing the
sandboxes) which the administrator wants to keep unassigned.  So if
the free space is less than this amount, no new jobs can be accepted.


log/file
--------


The absolute file name of the JobController log file.


log/level (5)
-------------


The level for the logging.



WorkloadManager
===============


pipeDepth (1)
-------------


The maximum size of the buffer between the dispatcher and worker
threads.


workerThreads (1)
-----------------


The size of the workerThread pool.


dispatcherType (filelist)
-------------------------


Defines the type of the input queue of requests.


inputFile
---------


Input queue of the requests for the WorkloadManager.


maxRetryCount (10)
------------------


The maximum number of times the WorkloadManager can try to re-schedule
and re-submit a job in case of system failures.


hostProxyFile
-------------


This must be the same as the X509_USER_PROXY value specified in the
edg-wl-ns start up script.


log/file
--------


The absolute file name of the JobController log file.


log/level (5)
-------------


The level for the logging.



