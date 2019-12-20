
#########################
NCM\::Component\::myproxy
#########################


****
NAME
****


myproxy:  NCM component to configure MyProxy server.


***********
DESCRIPTION
***********


The \ *myproxy*\  component manages the `/opt/edg/etc/edg`-myproxy.conf
file for the MyProxy server.


*********
RESOURCES
*********


flavor : string (required)
==========================


MyProxy configuration variant. Must be either 'edg' or 'glite'.

Default: edg


confFile : string (required)
============================


Configuration file for MyProxy. In edg variant, this is an intermediate configuration file used to generate the real one.

Default: `/opt/edg/etc/edg`-myproxy.conf


daemonName : string (required)
==============================


The MyProxy daemon name. Must be either 'myproxy' or 'myproxy-server'.

Default: myproxy


trustedDNs : list of string (optional, DEPRECATED)
==================================================


A list containing the list of DNs to trust for proxy renewal and retrieval.  This is
usually the DNs of all trusted resource brokers. When present, authorizedDNs and and defaultDNS must be ommitted.


authorizedDNs :  (optional)
===========================


A structure containing the following items, each one being a list of string:


- renewers
 
 Clients authorized to renew credentials.
 


- retrievers
 
 Clients authorized to retrieve credentials after providing the username/password used when the proxy was created.
 


- keyRetrievers
 
 Clients authorized to retrieved credentials (including the private key) after providing the username/password used when the proxy was created.
 


- trustedRetrievers
 
 Clients authorized to retrieve credentials without providing a username/password.
 


A structure containing the same list of items as the previous one.



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


1.2.2


********
SEE ALSO
********


ncm-ncd(1), myproxy-server.config(5)

