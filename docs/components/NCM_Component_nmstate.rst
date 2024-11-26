
#########################
NCM\::Component\::nmstate
#########################


****
NAME
****


network: New module to configure networking using nmstate and NetworkManager.
Most functions and logic is taken from network module to minimise changes to current network module.


***********
DESCRIPTION
***********


The \ *network*\  component sets the network settings through nmstate.
Configuration are created in yaml file at ``/etc/nmstate`` and applied using nmstatectl.
NetworkManager acts as the main (and currently the only) provider supported by nmstate.

New/changed settings are first tested by retrieving the latest profile from the
CDB server (using ccm-fetch).
If this fails, the component reverts all settings to the previous values. This is no different to network module.

During this test, a sleep value of 15 seconds is used to make sure the restarted network
is fully restarted (routing may need some time to come up completely).

Because of this, configuration changes may cause the ncm-ncd run to take longer than usual.

Be aware that configuration changes can also lead to a brief network interruption.

