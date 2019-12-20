
###############################
NCM\::Component\::pbsknownhosts
###############################


****
NAME
****


The \ *pbsknownhosts*\  component manages the configuration file
for the edg-pbs-knownhosts script.


***********
DESCRIPTION
***********


The \ *pbsknownhosts*\  component manages the configuration file for the
edg-pbs-knownhosts script.


*********
RESOURCES
*********


configfile (/opt/edg/etc/edg-pbs-knownhosts.conf)
=================================================


The location of the configuration file.  Normally this should not be
changed.


pbsbin (/usr/bin)
=================


The path to the pbs executables.


nodes ()
========


Space-separated list of additional nodes to add to known hosts
configuration file.  The default is the empty list.


keytypes (rsa1,rsa,dsa)
=======================


The types of ssh keys to generate.


knownhosts (/etc/ssh/ssh_known_hosts)
=====================================


The ssh known hosts file to update.


knownhostsscript (/opt/edg/sbin/edg-pbs-knownhosts)
===================================================


The script to run for generating the known hosts.


targets (optional, string[])
============================


Specify what configuration files should be generated. The default
is to generate a configuration for edg-pbs-knownhosts only, but
is can be set to also - or alternatively - generate the 
configuration for edg-pbs-shostsequiv.

The value is an array of strings that specify the disired 
behaviour: "pbsknownhosts/targets" = list("pbsknownhosts") will
generate the edg-pbs-knownhosts config only; "pbsknownhosts/targets" = 
list("shostsequiv") will generate edg-pbs-shostsequiv config only;
and "pbsknownhosts/targets" = list("pbsknownhosts","shostsequiv") will
generate both.


shostsConfigFile (optional, `/opt/edg/etc/edg`-pbs-shostsequiv.conf)
====================================================================


The location of the shosts-script configuration file.  Normally this 
should not be changed.


shosts (optional, `/etc/ssh/shosts.equiv`)
==========================================


The ssh shosts.equiv file to update


shostsscript (optional, `/opt/edg/sbin/edg`-pbs-shostsequiv)
============================================================


The script to run for generating shosts.equiv.