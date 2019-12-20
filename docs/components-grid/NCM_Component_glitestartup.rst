
##############################
NCM\::Component\::glitestartup
##############################


****
NAME
****


glitestartup : NCM component to configure startup of gLite services


***********
DESCRIPTION
***********


This NCM component allows to configure startup driver of gLite services. If there is a change to the startup driver configuruation
file, by default all services are restarted.


*********
RESOURCES
*********


`/software/components`/@COMP/configFile : string (required)
===========================================================


Configuration file path/name for startup driver.

Default : `/opt/glite/etc/config/scripts/gLite.services`


`/software/components`/@COMP/createProxy : boolean
==================================================


If true, create a grid proxy for the gLite user used to run the service.

Default : true


`/software/components`/@COMP/disableOutput : boolean (optional)
===============================================================


If true, redirect script output to `/dev/null.` For special cases where the output can trigger problems
(like those related to Python PIPE bugs).


`/software/components`/@COMP/disableError : boolean (optional)
==============================================================


Idem as disableOutput but for stderr.


`/software/components`/@COMP/initScript : string (required)
===========================================================


Name of startup script for gLite services.

Default : `/etc/rc.d`/init.d/gLite


`/software/components`/@COMP/postRestart : list (optional)
==========================================================


A list of nlist defining commands to execute after successfully restarting services and the expected status of these
commands. Each nlist accepts the following properties :


- cmd : command to execute.



- expectedStatus : if defined, must specify as a number the expected status of the command. The expected status is the status value that must be considered as a success. If undefined, no test is made on return value.



Default : None


`/software/components`/@COMP/restartEnv : list of string (optional)
===================================================================


If defined, must be a list of string, each element being a script name to source before restarting services.

Default : undefined


`/software/components`/@COMP/restartServices : boolean (optional)
=================================================================


If true, all services are restarted, even if there was no change to startup driver configuration file. If false, services are not
restarted even if the startup driver configuration file was changed. If not defined, all services are restarted if there is a change
in startup driver configuration.

Default : not defined.


`/software/components`/@COMP/scriptPaths : list of string (required)
====================================================================


List of paths where to look for a script matching service name.

Default : `/opt/glite/etc/init.d`


`/software/components`/@COMP/services : nlist of string
=======================================================


Nlist with one entry per service to start. Key is the service name,
value is an optional nlist. This nlist can contain the following element:


- args startup script arguments



Default : none



************
DEPENDENCIES
************


None.


****
BUGS
****


None known.


******
AUTHOR
******


Michel Jouvin <>


**********
MAINTAINER
**********


Michel Jouvin <>


*******
VERSION
*******


1.1.1


********
SEE ALSO
********


ncm-ncd(1)