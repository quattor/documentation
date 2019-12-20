
##############################
NCM\::Component\::condorconfig
##############################


****
NAME
****


The \ *condorconfig*\  component manages the configuration file of 
Condor.


***********
DESCRIPTION
***********


The \ *condorconfig*\  component manages the configuration file (default
is `/opt/condor/etc/condor.conf`) for Condor.  All of the condor
parameters are available with exactly the same name in Quattor.  See
the condor documentation for the names and descriptions of the
parameters.


*********
RESOURCES
*********


configfile (/opt/condor/etc/condor.conf)
========================================


The absolute file name of the configuration file.


user (edguser)
==============


The username to use for running condor.


