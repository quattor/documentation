
###############################
NCM\::Component\::FreeIPA\::CLI
###############################


***********
CLI FreeIPA
***********


Module to use as CLI to FreeIPA


***********
DESCRIPTION
***********


Module to use as CLI to FreeIPA, e.g. when initialising on existing host
or during kickstart.

Runs with default debug level 5.

Example command (one line)


.. code-block:: perl

     PERL5LIB=/usr/lib/perl perl -MNCM::Component::FreeIPA::CLI -w -e install --
         --realm MY.REALM --primary primary.example.com --otp abcdef123456
         --domain example.com --fqdn thishost.sub.example.com


