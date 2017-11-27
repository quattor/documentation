
### NAME

vomsclient: NCM component to manage VOMS client configuration

### DESCRIPTION

The _vomsclient_ component manages the configuration for the VOMS
clients.  This writes the VOMS server certificates to the vomsCertsDir
directory and the VOMS server parameters to the vomsServersDir
directory.

### RESOURCES

#### `/software/components/vomsclient/vomsCertsDir` (/etc/grid-security/vomsdir)

The directory to write the VOMS server certificates into.  If the
directory doesn't exist, it is created.  It will remove all managed
files and create new ones each time the configuration is done.

#### `/software/components/vomsclient/vomsServersDir` (/opt/edg/etc/vomses)

The directory to write the VOMS server parameters into.  If the
directory doesn't exist, it is created.  It will remove all managed
file and create new ones each time the configuration is done.

#### `/software/components/vomsclient/vos`

This is a named list of VOMS VO information.  Each key should be the
VO name. The value is a list of nlist : each nlist describes one VOMS server
supporting the VO. Supported properties for each VOMS server are described below.

#### VOMS server properties

Each VOMS server is described with a nlist. The following properties
can be used to describe one VOMS server.

### name (optional, deprecated)

The complete name of the VO, if the 'vos' key is an alias name. This
property is deprecated : it is recommended to use the complete name of the
VO as 'vos' key.

### host (required)

The complete hostname of the VOMS server.

### port (required)

The port number of the VOMS server.

### cert (required)

The certificate for the server.

### oldcert (optional)

The expiring certificate for the server. This allows smooth transition
between 2 certificates.

### DN (optional)

DN of VOMS server certificate

### issuer (optional)

DN of VOMS server certificate issuer.

### lscfile (optional)

Use LSC format instead of certificate to configure vomsCertsDir

### EXAMPLE

"/software/components/vomsclient/vos" = npush("somevo.example.org",
  list(nlist(
    "host","vo.somevo.example.org",
    "port","20000",
    "cert", <<EOF)));
\----BEGIN CERTIFICATE----
... encoded binary info ...
\----END CERTIFICATE----
EOF
