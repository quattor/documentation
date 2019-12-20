
########################
NCM\::Component\::xrootd
########################


****
NAME
****


xrootd : NCM component to manage Xrootd configuration.


***********
DESCRIPTION
***********


This component allows to manage configuration of Xrootd services.

The configuration description for Xrootd is made of 2 distinct parts:


- Hosts This is a description of all hosts participating to the Xrootd service with their role (disk server, redirector, federated redirector).



- Cluster-wide options These resources describe the configuration of the Xrootd cluster that applies to all the nodes participating to the service.



Cluster-wide options are found under configuration path `/software/components/xrootd.` For the
complete list of options, see the schema. The main ones are described here.

There are several subsets of options:


- General options These options are properties found directly under `/software/components/xrootd.`



- Service-specific options They are options that apply to a specific service or component of Xrootd. Examples are the DPM/Xrootd plugin, the token-based authentication, Xrootd instances. These subsets are resources located under  `/software/components/xrootd.`



Options can be required or optional. When they are required, if a default value is provided, it is not
necessary to define them explicitly: the default value will be used if they are not provided.


************
Xrootd hosts
************


This resource describes the hosts participating to the Xrootd cluster. They are specified as a 
nlist where the key is the host name and the value is a nlist specifying host specific options.
Valid properties in this nlist are:

roles : list of strings (required)
==================================


Specify the Xrootd roles instanciated on the host. Valid values are : disk, redir, fredredir.

Default : none



**********************
Xrootd general options
**********************


These options are properties found directly under `/software/components/xrootd/options.` Main ones
are described below.

authzLibraries: list of string (required)
=========================================


This option describes the list of authorization libraries (plugins) to use.

Default: none


configDir: string (required)
============================


This option described where the Xrootd configuration information is located. This can be either an 
absolute path or a path related to installDir (see below).

Default: etc/xrootd


installDir: string (required)
=============================


Directory parent of the Xrootd installation.

Default: /


daemonGroup: string (required)
==============================


Group that Xrootd daemons run under.

Default: none


daemonUser: string (required)
=============================


Userid that Xrootd daemons run under.

Default: none


MonALISAHost: string (optional)
===============================


MonALISA host to report Xrootd statistics to.

Default: none


monitoringOptions : string (optional)
=====================================


Options passed to xrootd.monitor directive for disk servers and local redirector.

Default : none


ofsPlugin: string (required)
============================


Specifies the Xrootd plugin to use for the file-system backend.

Default: Ofs


reportingOptions : string (optional)
====================================


Options passed to xrd.report directive for disk servers and local redirector.

Default : none


restartServices : boolean (required)
====================================


This flag indicated if Xrootd services must be restarted after a configuration change.

Default: true



****************
Xrootd instances
****************


There are two main services in a Xrootd cluster:


- xrootd Several instances of this service can coexist on the same host, one for each of its roles (disk, redirector, federated redirector). Information about these instances are found under  `/software/components/xrootd/options/xrootdInstances.` One xrootd instance must exist on every xrootd host.



- cmsd There must be one cmsd instance for each federation the Xrootd is participated in (a cmsd instance must exist matching each xrootd instance of type 'fedredir'). Information about these instances are found under  `/software/components/xrootd/options/cmsdInstances.`



In both cases, the properties (options) available are the same.

configFile: string (required)
=============================


The name of the Xrootd configuration file describing the instance configuration. This file must be located
in the directory pointed by configDir (see above).

Default: none


federation : string (optional)
==============================


Used by 'fedredir' instances only (cms and xrootd instances). This is the identifier (see Federations below) the redirector is
participating to.

Default: none


logFile: string (required)
==========================


Full path of the instance log file.

Default: none


type: list of strings (required)
================================


The type of the instance. Can be disk, redir and fedredir for xrootd service. And only fedredir for 
cmsd service.

Default: none



*************************
DPM/Xrootd plugin options
*************************


This set of options describes the configuration of the DPM Xrootd plugin. This set is optional and must
not be defined if the DPM/Xrootd plugin is not used. It is found under 
`/software/components/xrootd/options/dpm.`

Main options are described below.

coreMaxSize : long (optional)
=============================


Max size of core dump files.

Default: none


defaultPrefix: string (optional)
================================


Prefix to be added to every file path specified by users to make the actual file path.

Default: none


dpmConnectionRetry: long (optional)
===================================


Max number of retries when connecting to DPM service.

Default: none


dpmHost: string (required)
==========================


Name of the host running the DPM service (dpm daemon).

Default: none


dpnsConnectionRetry: long (optional)
====================================


Max number of retries when connecting to DPNS service.

Default: none


dpnsHost: string (required)
===========================


Name of the host running the DPNS service (dpm daemon).

Default: none


replacementPrefix: nlist of strings (optional)
==============================================


It allows to specify the actual path prefix to substitute (nlist value) to a user-specified path starting
by a string matching the nlist key. This option, if present, takes precedence over 
defaultPrefix (see above) if the path is matching. For example:

replacementPrefix = nlist('/cms', '/dpm/example.com/home/cms');

This will convert `/cms/myfile` to `/dpm/example.com`/home/cms/myfile.

Default: none



**************************
Token-based authentication
**************************


This set of options describes the configuration of token-based authorization. This set is optional and must
not be defined if token-based authentication is not enabled. It is found under 
`/software/components/xrootd/options/tokenAuthz.`

Main options are described below.

accessRules: list of nlist (required)
=====================================


This nlist allows to build the accessRules for token-based authentication, based on whether the
user is authenticated or not and other informations. See Xrootd documentation for details.

Each entry in the list is a nlist with the following required properties:


- path The Xrootd path the rule apply to. This is a string, it must be present and has no default.



- authenticated Operations allowed for authenticated users. This is a list of string, it must be present and has  no default



- unauthenticated Operations allowed for unauthenticated users. This is a list of string, it must be present and has no default



- cert
 
 A specific certificate that must be presented by the user for the rule to apply. This is a string, it must
 be present and default to '\*' (no restriction based on certificate).
 


- vo
 
 A specific VO that must be presented by the user (in the token) for the rule to apply. 
 This is a string, it must be present and default to '\*' (no restriction based on VO).
 



authzConf: string (required)
============================


Full path of the configuration file for token-based authorization.

Default: `/etc/grid`-security/xrootd/TkAuthz.Authorization


allowedFQANs: list of string (required)
=======================================


The VOMS FQANs that are matched in DPM ACLs when the token-based authorization is used.


authorizedPaths: list of string (required)
==========================================


The prefix of DPM paths that can be accessed when using token-based authorization.

Default: none


exportedPathRoot: string (required)
===================================


Xrootd path that is accessible through token-based authorization. This can be used to restrict
data accessible throgh this authorization to a subset of the data available in the whole cluster.

Default: none


exportedVOs: nlist (required)
=============================


List of VOs (retrieved from the token) allowed to access the XRootd cluster through token-based 
authorization. It is specified as a nlist where the key is the VO name and the value an 
optional nlist allowing to specify the path related to exportedPathRoot associated with the 
VO ('path' property). When empty, the VO name is used.

Note that it is strongly recommended to export only one VO with token-based authorization.

Default: none


principal : string (required)
=============================


The principal (user) to use to find the matching gridmap entry when token-based authentication is used.

Default: none


tokenPrivateKey string (required)
=================================


Full path of the token private key (that must be created outside of this configuration module).

Default: `/etc/grid`-security/xrootd/pvkey.pem


tokenPublicKey string (required)
================================


Full path of the token public key (that must be created outside of this configuration module).

Default: `/etc/grid`-security/xrootd/pubkey.pem


.. code-block:: perl

   "exportedVOs" : xrootd_component_exported_path{}
   "exportedPathRoot" : string




******************
Federation options
******************


For each Xrootd federation supported (taht need to be configured) on a given Xrootd node, the federation parameters are described under
`/software/components`//xrootd/options/federations. This is a nlist where the key is a federation identifier (arbitrary,
used to refer to the federation by 'federations' property of instances) and the value a nlist with the following possible properties.

federationCmsdManager : string (required)
=========================================


The federation cmsd manager (upper level cmsd) id. The format is : host.dom.ain+:port (note the +).

Default: none


federationXrdManager : string (required)
========================================


The federation xrootd manager (upper level xrootd redirector) id. The format is : host.dom.ain:port (note the +).

Default: none


n2nLibrary' : string (optional)
===============================


The name of the Name2Name library used in the federation and its parameters (library specific).

Default: none


namePrefix : string (optional
=============================


The path prefix of the local file names that are passed to the N2N library.

The federation cmsd manager id. The format is : host.dom.ain+:port (note the +).


localPort : long (required)
===========================


The port number of the cluster redirector participating to the federation.

Default: none


localRedirector : string (required)
===================================


Host:port of the cluster local redirector. Typically localhost:localPort.

Default: none


lfcHost : string (optional)
===========================


The optional LFC host name if N2N library relies on LFC.

Default: none


lfcConnectionRetry : long (optional)
====================================


Connection retry when trying to connect to LFC. Ignored if lfcHost is not defined. Typical value is 0.

Default: none (not defined explicitly)


lfcSecurityMechanism : string (optional)
========================================


Security mechanism to use when connecting to LFC. Ignored if lfcHost is not defined. Typical value is 'ID'.

Default : none


localRedirectParams : string (optional)
=======================================


The redirect parameters for the local redirector in the format expected by 'xrootd.redirect'
Xrootd configuration directive. Typically used to redirect to federation redirector for the VO supported
by the federation.

Default: none


monitoringOptions : string (optional)
=====================================


Options passed to xrootd.monitor directive for the federation redirector.

Default : none


redirectParams : string (optional)
==================================


The redirect parameters for the federation redirector in the format expected by 'xrootd.redirect'
Xrootd configuration directive.

Default: none


reportingOptions : string (optional)
====================================


Options passed to xrd.report directive for the federation redirector.

Default : none


validPathPrefix : string (optional)
===================================


The prefix of user paths that are accepted by the federation redirector.

Default: none



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


1.9.1


********
SEE ALSO
********


ncm-ncd(1)