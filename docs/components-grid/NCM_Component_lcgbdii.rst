
#########################
NCM\::Component\::lcgbdii
#########################


****
NAME
****


The \ *lcgbdii*\  component manages the configuration file of BDII service.


***********
DESCRIPTION
***********


The \ *lcgbdii*\  component manages the BDII configuration.


*********
RESOURCES
*********


Check schema for the full list of resources. Due to some changes in BDII configuration between all versions,
some resources marked optional in the schema for backward compatibility are in fact required to properly
configure recent BDII versions.

archiveSize : long (optional)
=============================


The number of updates that the changes should be logged (BDII v5 and later).


autoUpdate : string (yes or no)
===============================


Whether or not to auto-update.  Valid values are "yes" and "no".

Default : no


autoModify : string (yes or no)
===============================


Whether or not to automatically modify this file.

Default : no


bind : string
=============


The binding string.

Default: "mds-vo-name=local,o=grid"


breatheTime : long
==================


The time between LDAP queries.

Default: 60


configFile : string (required)
==============================


The location of the LCG BDII configuration file.

Default: `/opt/bdii/etc/bdii.conf`


dir
===


The base directory for the BDII code and configuration files.

Default: `/opt/bdii`


fixGlue : string (yes or no, optional)
======================================


Fixes some common schema errors like publishing duplicate attributes ()BDII v5 and later, recommeded value : yes).


isCache : string (yes or no)
============================


Whether or not to reject entries which already match the binding string.

Default : no


ldifDir : string
================


Location of GIP static ldfi files. New and required in BDII v5 and later.


logFile : string (optional)
===========================


The location of the LCG BDII log file. This property is required for BDII v5.

Default: none


logLevel : string (one of ERROR, WARNING, INFO, DEBUG)
======================================================


BDII verbosity level. New in BDII v5 (recommended value: ERROR)

Default: none.


modifyDN : string (yes or no)
=============================


Whether or not this BDII fixes DNs to match binding string.

Default : no


pluginDir : string
==================


Location of GIP plugins. New and required in BDII v5 and later.


port : port number
==================


Port used by BDII (v5 and later). Exclusive of portRead and portsWrite.

Default: none


portRead : port number
======================


The port to read from (version <= 4).

Default: none


portsWrite : list of port numbers
=================================


The list of ports to write to (version <= 4).

Default: none


providerDir : string
====================


Location of GIP providers. New and required in BDII v5 and later.


RAMDisk : string (yes or no, optional)
======================================


Use a RAM disk for the database files. It is advisable to have at least 4GB of RAM.
(BDII_top v3.2.10-3 and later, recommeded value : yes).


readTimeout : long (optional)
=============================


Time to wait for LDAP sources to return. New in BDII v5 (typically 300).


schemaFile
==========


Name of file listing the schemas used by BDII.  This is required for LCG 2.5.0 or above.

Default: `/opt/bdii/etc/schemas`


schemas : list of strings (optional)
====================================


List of file names for the schema files used.

Default: none


searchFilter : string (optional)
================================


The LDAP filter.


searchTimeout : long (optional)
===============================


The LDAP timeout in seconds. Deprecated in BDII v5.


slapadd : string (optional)
===========================


The location of the slapadd executable. Deprecated in BDII v5 and later.


slapd : string (optional)
=========================


The location of the slapd executable. Deprecated in BDII v5 and later.


slapdConf : string
==================


The location of slapd configuration file to use.

Default:  `/opt/bdii/etc/glue`-slapd.conf


slapdDebugLevel : long (0 to 5)
===============================


slapd verbosity level. Deprecated in BDII v5 and later.


updateLdif
==========


The URL for the update LDIF file.


updateUrl
=========


The URL for the update file.


urls (optional)
===============


A hash containing all of the update URLs.  The keys are for
documentation purposes only.

This resource is required for BDII v4 and later.


user : string
=============


The default user for running the BDII daemon.

Default: edguser



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


Charles Loomis <>, Michel Jouvin <>


*******
VERSION
*******


2.7.2


********
SEE ALSO
********


ncm-ncd(1)

