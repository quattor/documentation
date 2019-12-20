
###########################
NCM\::Component\::pbsserver
###########################


****
NAME
****


pbsserver: NCM component to configure partially the pbs (torque) server.


***********
DESCRIPTION
***********


The \ *pbsserver*\  component configures the pbs (torque) server. 
Unsetting attributes of nodes doesn't work (yet).


*********
RESOURCES
*********


pbsroot (/var/spool/pbs)
========================


The absolute path to the pbs root directory.


binpath (/usr/bin)
==================


The absolute path to the pbs binaries qmgr and pbsnodes.


submitfilter
============


The content of the submit filter.  This file will be written to the
file $pbsroot/submit_filter and a reference to this put into the
$pbsroot/torque.cfg file.  If this is not specified, the reference to
the script will be removed.


env
===


A named list with the environment to use for the pbs server.  As a
security feature, pbs removes the current environment when it starts
and substitutes the environment defined in this file.  Typical things
to set are the PATH and LANG.  Optionally for torque, the variable
TORQUEKEEPCOMPLETED can be set to keep jobs in a "completed" state for
5 minutes after they complete.  This is very useful for debugging
problems.


"/software/components/pbsserver/server" ? pbs_server
====================================================


Sets the configuration of the server. Structure as follows:

\ *"/software/components/pbsserver/server/manualconfig" : boolean*\ 

Set to false gives complete control to ncm-pbsserver, meaning that it
will configure defined attributes and will remove existing non-defined
ones. Set to true will configure defined ones, but not remove existing
non-defined ones, thus allowing local configuration of other
attributes.

\ *"/software/components/pbsserver/server/attlist" ? pbs_server_attlist*\ 

A named list with attributes to be set for the server through qmgr.


"/software/components/pbsserver/queue" ? pbs_queuelist
======================================================


Sets the configuration of the queue. Structure as follows:

\ *"/software/components/pbsserver/queue/manualconfig" : boolean*\ 

Same as `/software/components/pbsserver/server/manualconfig`, but will
remove queues completely if set to false.

\ *"/software/components/pbsserver/queue/queuelist" ? pbs_queue*\ 

A named list where the key is the name of the queue and the value of
the type pbs_queue. This type has also a manualconfig to allow manual
configuration of the attributes of the queue. It also can have an
entry attlist of type pbs_queue_attlist, which is a named list with
the attributes of that queue.


"/software/components/pbsserver/node" ? pbs_node_list
=====================================================


Analog to `/software/components/pbsserver/queue`, with entries
manaulconfig and nodelist. Nodelist is a named list with the FQHN of
the workernode as key and as value the type pbs_node, consisting of a
manualconfig and an attlist of type pbs_node_attlist.


