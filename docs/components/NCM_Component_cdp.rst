
#####################
NCM\::Component\::cdp
#####################


****
NAME
****


The \ *cdp*\  component manages the configuration file
``/etc/cdp-listend.conf.``


***********
DESCRIPTION
***********


The \ *cdp*\  component manages the configuration file for the
cdp-listend daemon.


********
EXAMPLES
********



.. code-block:: perl

     include 'components/cdp/config';
     prefix "/software/components/cdp";
     "fetch" = "/usr/sbin/ccm-fetch";
     "fetch_smear" = 30;


