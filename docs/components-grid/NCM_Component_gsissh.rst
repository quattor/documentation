
########################
NCM\::Component\::gsissh
########################


****
NAME
****


gsissh: NCM component to manage gsissh configuration file(s)


***********
DESCRIPTION
***********


The \ *gsissh*\  component writes manages the configuration for 
both the client and server sides of the GSI-enabled SSH daemon.


*********
RESOURCES
*********


`/software/components/gsissh/server`
====================================


An optional nlist with the server-side configuration.  If not
specified, then the server is not configured.

`/software/components/gsissh/server/port`
-----------------------------------------


The port to use for the daemon.  This is mandatory.


`/software/components/gsissh/server/options`
--------------------------------------------


An nlist giving the options to use.  Typical options are:
PermitRootLogin, RSAAuthentication, PubkeyAuthentication,
PasswordAuthentication, ChallengeResponseAuthentication, which take
yes/no values.



`/software/components/gsissh/client/options`
============================================


An optional nlist giving the client options to use.  Typical options
are: GssapiAuthentication, GssapiKeyExchange, and 
GssapiDelegateCredentials which take yes/no values.  The client is
always configured even if there are no options.



*******
EXAMPLE
*******



.. code-block:: perl

     "/software/components/gsissh/server/port" = 1975;
     "/software/components/gsissh/server/options" =
           dict(
               "PermitRootLogin", "no",
               "RSAAuthentication", "no",
               "PubkeyAuthentication", "no",
               "PasswordAuthentication", "no",
               "ChallengeResponseAuthentication", "no");