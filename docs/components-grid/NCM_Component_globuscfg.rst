
###########################
NCM\::Component\::globuscfg
###########################


****
NAME
****


globuscfg: Configure Globus services.


***********
DESCRIPTION
***********


The \ *globuscfg*\  component configures the globus services. It manages
the `/etc/sysconfig/globus` and globus configuration files. In
addition, it will start the specified Globus services.


*********
RESOURCES
*********



- ``/software/components/globuscfg/sysconfigUpdate`` : boolean
 
 If false, ``/etc/sysconfig/globus`` is not updated. Must be set to
 false if you want to manage `/etc/sysconfig/globus` with another component
 (e.g. ncm-sysconfig).
 
 D : true
 


- ``/software/components/globuscfg/GLOBUS_LOCATION``
 
 The root of the Globus software tree. By default this is ``/opt/globus``.
 


- ``/software/components/globuscfg/GLOBUS_CONFIG``
 
 The full path to the Globus configuration file. Defaults to
 ``/etc/globus.conf``.
 


- ``/software/components/globuscfg/globus_flavor_name``
 
 The globus "flavor" to use. There is no default. A typical value is
 gcc32dbg.
 


- ``/software/components/globuscfg/services``
 
 The list of Globus services to restart after a configuration.
 


- ``/software/components/globuscfg/x509_user_cert``



- ``/software/components/globuscfg/x509_user_key``
 
 The path to the host certificate and key. These have no default as
 there are some machines which do not require the security
 infrastructure to be installed.
 


- ``/software/components/globuscfg/gridmap``
 
 The path to the grid-mapfile. This has no default as there are some
 machines which do not require the security infrastructure to be
 installed.
 


- ``/software/components/globuscfg/GLOBUS_TCP_PORT_RANGE``
 
 The port range that the gatekeeper and gridftp will use to open
 up listening services for inbound tcp connections. eg 50000,52000
 


- ``/software/components/globuscfg/GLOBUS_UDP_PORT_RANGE``
 
 The port range that the gatekeeper and gridftp will use to open
 up listening services for inbound udp connections. eg 50000,52000
 


- ``/software/components/globuscfg/gridmapdir``
 
 The path to the grid-mapfile. This has no default as there are some
 machines which do not require the security infrastructure to be
 installed.
 


- ``/software/components/globuscfg/mds/globus_flavor_name``
 
 The globus "flavor" to use for MDS will use global value unless specified.
 


- ``/software/components/globuscfg/mds/user``
 
 The user with which to run the MDS daemons (default: root).
 


- ``/software/components/globuscfg/mds/x509_user_cert``



- ``/software/components/globuscfg/mds/x509_user_key``
 
 The path to the certificate and key to use for MDS. Host credentials
 will be used if not specified.
 


- ``/software/components/globuscfg/mds/gris/suffix``
 
 The suffix to use for the GRISes. Defaults to ``""Mds-Vo-name=local,o=grid""``.
 Double quotes MUST appear as part of the value.
 


- ``/software/components/globuscfg/mds/gris/provider``
 
 A table of GRIS information providers to run within the MDS. By
 default the name of each provider is the name of the info provider
 executable (in the default area), so for example in the case of
 
 
 .. code-block:: perl
 
      "/software/components/globuscfg/mds/gris/provider/xyz"=""
 
 
 "xyz" will be taken, as the name of the executable.
 You may optionally specify a fully-qualified executable name to
 override this default. The parameter to set is, for example,
 "provider_edg" for the edg information provider.
 


- ``/software/components/globuscfg/mds/gris/registration``
 
 The \ *list*\  of GIISes to which the GRISes should register, so it
 has entries labelled with numbers. These entries are have
 further entries like \ *regname*\ , \ *reghost*\ , \ *regport*\ , \ *regperiod*\ ,
 and \ *ttl*\ . These are optional. Default values of these parameters
 can be changed this using them. The \ *regperiod*\  and
 \ *ttl*\  should be specified as a pair with \ *ttl*\  at least twice that
 of \ *regperiod*\ . The name of the GIIS defaults
 entry \ *recordname*\ , which is obligatory for every element.
 


- ``/software/components/globuscfg/mds/giis/allowedregs``
 
 The \ *list*\  of local GIISes to run. As for lists, entries which
 represent GIISes have numbers as names. They have an obligatory
 field (\ *recordname*\ ), the identifier name of the entry. This
 will be taken as the default value for \ *name*\  parameter, but can be
 overriden by specifying this one explicitly. See example.
 


- ``/software/components/globuscfg/mds/giis/allowedregs/_number_/allowreg``
 
 The list of allowed host:port pairs which may register to this
 giis. This is a sub-parameter of the giis.
 


- ``/software/components/globuscfg/mds/giis/registration``
 
 To register a local GIIS to another GIIS specify explicitly at least
 the \ *regname*\  sub-parameter.  Additionally, you may also specify
 \ *reghost*\ , \ *regport*\ , \ *regperiod*\  and \ *ttl*\ . The parameter \ *reghost*\  is
 required for a remote GIIS.  Either the same tag as on the giis line
 must be used, or the tag variable can be specified.
 
 Multiple registrations for a local GIIS can be done by creating a
 dummy entry and explicitly specifying the tag and \ *name*\ 
 parameters.
 
 The \ *regperiod*\  and \ *ttl*\  should be specified as a pair with \ *ttl*\ 
 at least twice that of \ *regperiod*\ .
 


- ``/software/components/globuscfg/gridftp/globus_flavour_name``
 
 The globus "flavor" to use for GridFTP will use global value unless
 specified.
 


- ``/software/components/globuscfg/gridftp/X509_USER_CERT``



- ``/software/components/globuscfg/gridftp/X509_USER_KEY``
 
 The path to the certificate and key to use for GridFTP. Host credentials
 will be used if not specified.
 


- ``/software/components/globuscfg/gridftp/ftpd``
 
 The full path to the GridFTP daemon. Normally this is not specified
 as the default is usually correct.
 


- ``/software/components/globuscfg/gridftp/port``
 
 The port number to use for the GridFTP daemon. The default is 2811.
 


- ``/software/components/globuscfg/gridftp/umask``
 
 The umask to use for the GridFTP daemon. The default is 002.
 


- ``/software/components/globuscfg/gridftp/log``
 
 The full path to the log file for the GridFTP daemon. This defaults
 to the area ``/var/log``.
 


- ``/software/components/globuscfg/gridftp/user``
 
 The user with which to run the GridFTP daemon. Will default to root.
 


- ``/software/components/globuscfg/gridftp/options``
 
 This will override all options for the GridFTP daemon. Use only if
 you really know what you are doing.
 


- ``/software/components/globuscfg/gatekeeper/globus_gatekeeper``
 
 The executable name for the gatekeeper.
 


- ``/software/components/globuscfg/gatekeeper/extra_options``
 
 Additional options to pass to the gatekeeper.
 


- ``/software/components/globuscfg/gatekeeper/globus_flavor_name``
 
 The globus "flavor" to use for the gatekeeper will use global value
 unless specified.
 


- ``/software/components/globuscfg/gatekeeper/user``
 
 The user name to use to run the gatekeeper.
 


- ``/software/components/globuscfg/gatekeeper/port``
 
 The port to use for the gatekeeper. (This defaults to 2119 if not
 specified.)
 


- ``/software/components/globuscfg/gatekeeper/logfile``
 
 The location of the log file for the daemon. (Default depends on
 whether user is specified.)
 


- ``/software/components/globuscfg/gatekeeper/jobmanagers``
 
 The \ *list*\  of job managers to use for this gatekeeper. The fork job
 manager is required (and required to be the default), so only non-fork
 job managers need to be specified.
 


- ``/software/components/globuscfg/gatekeeper/jobmanagers/_entryNo_/recordname``
 
 Obligatory parameter, identifier string for a certain job manager.
 


- ``/software/components/globuscfg/gatekeeper/jobmanagers/_entryNo_/type``
 
 Mandatory option giving the type of LRMS. E.g. pbs, lsf, etc.
 


- ``/software/components/globuscfg/gatekeeper/jobmanagers/_enrtyNo_/job_manager``
 
 Name of job manager executable.
 


- ``/software/components/globuscfg/gatekeeper/jobmanagers/_entryNo_/job_manager_path``
 
 Path to the job manager executable. Only needs to be specified if it
 is in a non-standard location.
 


- ``/software/components/globuscfg/gatekeeper/jobmanagers/_entryNo_/extra_config``
 
 Extra configuration options needed by the job manager.
 



*******
EXAMPLE
*******



.. code-block:: perl

     "/software/components/globuscfg/globus_flavor_name" = "gcc32dbg";
 
     "/software/components/globuscfg/GLOBUS_LOCATION" = "/opt/globus";
 
     "/software/components/globuscfg/GLOBUS_CONFIG" = "/etc/globus.conf";
 
     "/software/components/globuscfg/services" =
     list(" globus-mds", "globus-gridftp");
 
     "/software/components/globuscfg/mds/user" = "mdsuser";
 
     "/software/components/globuscfg/gris/provider/globus-gris" = "";
 
     "/software/components/globuscfg/gris/provider/othergrid" =
                         "/opt/othergrid/othergrid.info";
 
     "/software/components/globuscfg/gris/registration/0/recordname" =  "local";
 
     "/software/components/globuscfg/gris/registration/0/regname" =  "localreg";
 
     "/software/components/globuscfg/giis/allowedregs/0/recordname" =  "local";
 
     "/software/components/globuscfg/mds/giis/allowedregs/0/allowreg" = "hostname:port";
 
     "/software/components/globuscfg/mds/giis/registration/remote/name" = "local";
 
     "/software/components/globuscfg/mds/giis/registration/remote/regname" = "somecountry";
 
     "/software/components/globuscfg/mds/giis/registration/remote/reghost" =
     "giis.someplace.com";
 
     "/software/components/globuscfg/mds/giis/registration/remote/regport" = 2135;
 
     "/software/components/globuscfg/mds/giis/registration/remote/regperiod" = 40;
 
     "/software/components/globuscfg/mds/giis/registration/remote/ttl"= 40;
 
     "/software/components/globuscfg/gridftp/user" = "ftpuser";
 
     "/software/components/globuscfg/gatekeeper/jobmanagers/0/recordname" = "JobManager";
 
     "/software/components/globuscfg/gatekeeper/jobmanagers/0/extra_config" = "extra_configs";


This changes the default location of the Globus software and tells the
component to manage the MDS and GridFTP daemons. Two information
providers (GRISes) are configured which register with the "local"
GIIS. The local GIIS then registers with the given remote GIIS.  The
user with which to run the GridFTP daemon is set to ftpuser while the
one for MDS is mdsuser.

