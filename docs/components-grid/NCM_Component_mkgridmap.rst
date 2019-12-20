
###########################
NCM\::Component\::mkgridmap
###########################


****
NAME
****


mkgridmap:  NCM component to configure edg-mkgridmap.conf for mkgridmap.


***********
DESCRIPTION
***********


The \ *mkgridmap*\  component manages the configuration file (e.g. `/opt/edg/etc/edg`-mkgridmap.conf) for mkgridmap.
It can handle several mapfiles and support two distinct mapfile format :


* edg : the traditional format associating DNs with pool accounts



* lcgdm : a mapfile to associate DNs to VO name. It is used by LCG products like DPM and LFC to handle authorization for users not authenticated with VOMS (grid-proxy-init or voms-proxy-init without -voms).




*********
RESOURCES
*********


entries : nlist
===============


A nlist of mapfile entries. The name of the entry is informational only. The entry resources are described
below.


lcmaps : nlist (optional)
=========================


This nlist describes lcmaps gridmapfile and groupmapfile to update. The entry resources are described
below.


voList : list (optional)
========================


This list specifies the VO to process, and the order in which they will appear. If not present or undefined, defaults to all VOs defined in the configuration (/system/vo), sorted by name.



****************
LCMAPS RESOURCES
****************


flavor : string
===============


This property indicates LCMAPS gridmapfile/groupmafile format. It can be 'edg' or 'glite'. When format is 'glite', FQANs 
are taken literally from configuration : they must be valid VOMS FQAN in standard format. When format is 'edg', FQANs
in configuration are converted into EDG format (/VO=vo_name/GROUP=.../ROLE=...).

Default : glite (no conversion)


lcmaps/gridmapfile : string (required)
======================================


The full path to the LCMAPS gridmapfile.

Default : `/opt/edg/etc/lcmaps/gridmapfile`


lcmaps/groupmapfile : string (required)
=======================================


The full path to the LCMAPS groupmapfile.

Default : `/opt/edg/etc/lcmaps/groupmapfile`



***********************
MAPFILE ENTRY RESOURCES
***********************


mkgridmapconf
=============


The location of the edg-mkgridmap.conf file, by default
`/opt/edg/etc/edg`-mkgridmap.conf


command
=======


The command to run to regenerate the gridmap file.  If provided, this
command will be run whenever changes to the configuration occur.


groups
======


A list of group entries in the edg-mkgridmap.conf file. For each group
uri_<group> and user_<group> can be defined to specify the collection
of users at a URI that should be mapped to a particular user.


auths
=====


A list of auth entries in the edg-mkgridmap.conf file. For each auth line
a uri_<auth> should be defined.


lcuser
======


What the lcuser should be defined as.


allow
=====


A pattern match of certs that should be permitted in the grid-mapfile.


deny
====


A pattern match of certs that should be denied in the grid-mapfile.

Note the allow allways occurs, if it is defined at all, in the mkgridmap.conf
file before the deny rule. Read man edg-mkgridmap.conf for the consequences of
this.


gmflocal
========


One or more local grid-mapfile(s) to be imported in the generated grid-mapfile, where they will override
other entries. By default <edgcfg.location>/etc/grid-mapfile-local. The entry
can be either a string (default), or a list of strings (in which case the existing entry will have to
be null-ified beforehand).


overwrite
=========


By default set to yes. If set to no the local grid-mapfile will not be
overwritten if it already exists.


locals
======


A list for which each element has the values of cert_<local> and 
user_<local>. This will add mappings to the (first) grid-mapfile-local defined
above.


