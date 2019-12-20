
##########################
NCM\::Component\::libvirtd
##########################


***********
DESCRIPTION
***********


The \ *libvirtd*\  component manages the configuration of the
the libvirtd daemon.


************************
CONFIGURATION PARAMETERS
************************


The base path for all of the configuration parameters is
    `/software/components/libvirtd.`  The following sections describe the
    elements that are permitted directly below this base path.  With
    further parameters described in each section.  All parameters are
    optional.  Except the configuration file location.

libvirtd_config (R '/etc/libvirt/libvirtd.conf')
================================================


This string defines the location of the libvirtd configuration file.


network
=======


This sections contains the networking parameters.


* listen_tls: 0 or 1, enabled by default



* listen_tcp: 0 or 1, disabled by default



* tls_port: port number (16514) or service name



* tcp_port: port number (16509) or service name



* listen_addr (type_hostname): IPv4/v6 address or hostname



* mdns_adv: 0 or 1, enabled by default



* mdns_name: default string is "Virtualization Host HOSTNAME"




socket
======


This section contains the configuration for unix sockets.


* unix_sock_group: restricted to root by default



* unix_sock_ro_perms: octal string, default allows any user



* unix_sock_rw_perms: octal string



* unix_sock_dir: directory of created sockets




authn
=====


This section contains the authentication parameters.


* auth_unix_ro: ``'none|sasl|polkit'``, default anyone



* auth_unix_rw: ``'none|sasl|polkit'``, default polkit



* auth_tcp' ? ``'none|sasl'``, should be 'sasl' for production



* auth_tls' ? ``'none|sasl'``




tls
===


This section contains the parameters for TLS.


* key_file: full path to key file



* cert_file: full path to certificate file



* ca_file: full path to certificate authority certificate



* crl_file: fall path to CRL




authz
=====


This section contains the authorization parameters.


* tls_no_verify_certificate: 0 or 1, defaults to verification



* tls_allowed_dn_list: list of allowed DNs



* sasl_allowed_username_list: list of allowed usernames




processing
==========


This section contains the parameters used to control the processing.


* max_clients: maximum number of clients



* min_workers: minimum number of workers



* max_workers: maximum number of workers



* max_requests: maximum number of requests



* max_client_requests: maximum number of client requests




logging
=======


This section contains the parameters used to control the logging.


* log_level: 4=errors,3=warnings,2=info,1=debug,0=none



* log_filters: list of filters, see man for format



* log_outputs: list of outputs, see man for format




