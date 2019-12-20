
########################
NCM\::Component\::gmetad
########################


***********
DESCRIPTION
***********


The \ *gmetad*\  component manages Ganglia's gmetad daemon.
This daemon collects performance information from various nodes and stores it in a RRD database.

GMETAD
======


The configuration of gmetad is stored in the file ``/etc/gmetad.conf``.

The schema for this component is very similar to the options in the configuration file.


* ``/software/components/gmetad/data_source/[srcindex]/name`` : string
 
 Name of the data source.
 


* ``/software/components/gmetad/data_source/[srcindex]/polling_interval`` : long(1..)
 
 Optional polling interval for the data source, in seconds.
 


* ``/software/components/gmetad/data_source/[srcindex]/host/[hostindex]/address`` : type_hostname
 
 Host name or IP address per machine serving the data source.
 


* ``/software/components/gmetad/data_source/[srcindex]/host/[hostindex]/port`` : type_port
 
 Optional port per machine serving the data source.
 


* ``/software/components/gmetad/debug_level`` : long(0..)
 
 Optional level of debug output for the daemon.
 


* ``/software/components/gmetad/scalability`` : string
 
 Optional flag to enable or disable scalability mode. 
 Valid values are ``on`` and ``off``.
 


* ``/software/components/gmetad/file`` : string
 
 Mandatory field specifying the location of the the configuration file.
 For Ganglia 3.0, this should be ``/etc/gmetad.conf``
 and for Ganglia 3.1, it should be ``/etc/ganglia/gmetad.conf``.
 


* ``/software/components/gmetad/gridname`` : string
 
 Optional name of the grid.
 


* ``/software/components/gmetad/authority`` : type_absoluteURI
 
 Optional authority URL for this grid.
 


* ``/software/components/gmetad/trusted_hosts`` : type_hostname[]
 
 Optional list of trusted hosts.
 


* ``/software/components/gmetad/all_trusted`` : string
 
 Optional field to enable trust of all hosts.
 Valid values are ``on`` and ``off``.
 


* ``/software/components/gmetad/setuid`` : string
 
 Optional flag to control setuid mode of the daemon.
 Valid values are ``on`` and ``off``.
 


* ``/software/components/gmetad/setuid_username`` : string
 
 Optional name of the user account running the daemon.
 


* ``/software/components/gmetad/xml_port`` : type_port
 
 Optional port on which gmetad will answer requests for XML.
 


* ``/software/components/gmetad/interactive_port`` : type_port
 
 Optional port on which gmetad will answer queries for XML.
 


* ``/software/components/gmetad/server_threads`` : long(1..)
 
 Optional number of threads answering XML requests.
 


* ``/software/components/gmetad/rrd_rootdir`` : string
 
 Optional directory where gmetad stores its RRD databases.
 



