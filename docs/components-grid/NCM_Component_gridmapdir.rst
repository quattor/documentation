
############################
NCM\::Component\::gridmapdir
############################


****
NAME
****


The \ *gridmapdir*\  component manages the gridmapdir directory.


***********
DESCRIPTION
***********


The \ *gridmapdir*\  component manages the gridmapdir directory used for the
mapping of pool accounts.


*********
RESOURCES
*********


gridmapdir (required)
=====================


The location of the configuration file.  Normally this should not be
changed.


poolaccounts (required)
=======================


An nlist with the pool account prefix as the name and a long as the
size of the pool.


sharedGridmapdir : string (optional)
====================================


If defined must indicate the path of a shared gridmapdir. In this case, gridmapdir as defined in 'gridmapdir' property
is made a symlink of this directory.



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


Charles Loomis <>


**********
MAINTAINER
**********


Michel Jouvin <>


*******
VERSION
*******


2.0.1


********
SEE ALSO
********


ncm-ncd(1)

