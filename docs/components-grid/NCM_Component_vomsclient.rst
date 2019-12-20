
############################
NCM\::Component\::vomsclient
############################


****
NAME
****


vomsclient: NCM component to manage VOMS client configuration


***********
DESCRIPTION
***********


The \ *vomsclient*\  component manages the configuration for the VOMS
clients.  This writes the VOMS server certificates to the vomsCertsDir
directory and the VOMS server parameters to the vomsServersDir
directory.


*******
EXAMPLE
*******



.. code-block:: perl

     "/software/components/vomsclient/vos" = npush("somevo.example.org",
         list(dict(
             "host", "vo.somevo.example.org",
             "port", "20000",
             "cert", <<EOF)));
             ----BEGIN CERTIFICATE----
             ... encoded binary info ...
             ----END CERTIFICATE----
         EOF


