
#######################
NCM\::Component\::wmslb
#######################


****
NAME
****


wmslb : NCM component to configure gLite  WMS and LB


***********
DESCRIPTION
***********


This NCM component allows to configure gLite WMS and LB.


*********
RESOURCES
*********


`/software/components`/@COMP/envScript : string (required)
==========================================================


Name of the shell script containing environment variables used by WMS/LB startup scripts to configure the services.

Default : `/etc/profile.d`/glite-wms-vars.sh


`/software/components`/@COMP/env : nlist of string (optional)
=============================================================


Each nlist element defines an environment variable to be added to envScript. Key is the variable name, value is variable value.
For the complete list of supported variables and their default values, see schema.tpl.

Default : see schema.tpl


`/software/components`/@COMP/services : nlist (optional)
========================================================


Per service configuration. For the list of supported services, see schema.tpl.

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


2.2.0


********
SEE ALSO
********


ncm-ncd(1)