
######################
NCM\::Component\::lcas
######################


****
NAME
****


lcas: NCM component to manage LCAS configuration file(s)


***********
DESCRIPTION
***********


The \ *lcas*\  component writes the LCAS configuration file(s). The
primary file is the LCAS database, listing the plugin modules
to be called (in the order specified in the profile).

Optionally, it can write the module configuration files as well
(as just plain files, one line for every entry in the content
list). The header can be suppressed, if ever there is a module
that chokes on the pound-sign comments at the top.

The \ *lcas*\  component can manage several different LCAS databases and associated module
configuration files.


**************
MAIN RESOURCES
**************


`/software/components/lcas/dbpath`
==================================


Deprecated. Mutually exclusive with `/software/components/lcas/db.`


`/software/components/lcas/module`
==================================


Deprecated. Mutually exclusive with `/software/components/lcas/db.`


`/software/components/lcas/db` : list (optional)
================================================


List of LCAS databases and associated module configaration files to configure. For each database,
the following attributes can be specified.

path : string (required)
------------------------


The database file name. This attribute is required for any database entry.

Default: none.


module : list (optional)
------------------------


A list of each module to configure in the database, with their arguments and optionally their
associated configuration file. See next section for supported module attributes.

Default: none




****************
MODULE RESOURCES
****************


For each module, the following attributes can be specified.

path : string (required)
========================


The plugin module file name. The path may be relative to the LCAS search path but it is
recommended to specify a full path. This attribute is required for any module.

Default: none


args : string (optional)
========================


Arguments to this module (like: the name of the module's config file).

Default: none


conf : nlist (optional)
=======================


Optional: write out the contents of a single configuration file
for this plugin module. The following attributes (nlist keys) are available
for the configuration file.

path : string (required)
------------------------


Location (absolute path) of the module configuration file. This attribute
is required if a configuration file is configured.

Default: none



noheader : boolean (required)
=============================


When set to true, suppress the initial comments normally added at the head of the configuration file.
This attribute is required if a configuration file is configured.

Default: false (header added)


content : list of string (optional)
===================================


Configuration file content as a list of string. Each list element will be added to
the file as a separate line, keeping the specified order.



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


David Groep <>


**********
MAINTAINER
**********


David Groep <>, Michel Jouvin <>


*******
VERSION
*******


1.1.0


********
SEE ALSO
********


ncm-ncd(1)