
#########################
NCM\::Component\::network
#########################


****
NAME
****


network: Configure Network Settings


***********
DESCRIPTION
***********


The \ *network*\  component sets the network settings through ``/etc/sysconfig/network``
and the various files in ``/etc/sysconfig/network-scripts``.

New/changed settings are first tested by retrieving the latest profile from the
CDB server (using ccm-fetch).
If this fails, the component reverts all settings to the previous values.

During this test, a sleep value of 15 seconds is used to make sure the restarted network
is fully restarted (routing may need some time to come up completely).

Because of this, configuration changes may cause the ncm-ncd run to take longer than usual.

Be aware that configuration changes can also lead to a brief network interruption.


********
EXAMPLES
********


CHANNEL BONDING
===============


To enable channel bonding with quattor using devices eth0 and eth1 to form bond0, proceed as follows:


.. code-block:: perl

     include 'components/network/config';
     prefix "/system/network/interfaces";
     "eth0/bootproto" = "none";
     "eth0/master" = "bond0";
 
     "eth1/bootproto" = "none";
     "eth1/master" = "bond0";
 
     "bond0" = NETWORK_PARAMS;
     "bond0/driver" = "bonding";
     "bond0/bonding_opts/mode" = 6;
     "bond0/bonding_opts/miimon" = 100;
 
     include 'components/modprobe/config';
     "/software/components/modprobe/modules" = append(dict("name", "bonding", "alias", "bond0"));
 
     "/software/components/network/dependencies/pre" = append("modprobe");


(see ``<kernel>/Documentation/networking/bonding.txt`` for more info on the driver options)


VLAN support
============


Use the ``vlan[0-9]{0-4}`` interface devices and set the explicit device name and physdev.
The VLAN ID is the number of the '.' in the device name.
`` physdev `` is mandatory for ``vlan[0-9]{0-4}`` device.

An example:


.. code-block:: perl

     prefix "/system/network/interfaces";
     "vlan0" = VLAN_NETWORK_PARAMS;
     "vlan0/device" = "eth0.3";
     "vlan0/physdev" = "eth0";



IPv6 support
============


An example:


.. code-block:: perl

     prefix "/system/network";
     "ipv6/enabled" = true;
     "ipv6/default_gateway" = "2001:678:123:e030::1";
     "interfaces/eth0/ipv6_autoconf" = false;
     "interfaces/eth0/ipv6addr" = "2001:610:120:e030::49/64";
     "interfaces/eth0/ipv6addr_secondaries" = list(
         "2001:678:123:e030::20:30/64",
         "2001:678:123:e030:172:10:20:30/64",
         );



