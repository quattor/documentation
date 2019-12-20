
##################################
NCM\::Component\::OpenNebula\::AII
##################################


****
NAME
****


``NCM::Component::OpenNebula::AII`` adds ``AII`` hook
to generate the required resources and templates
to instantiate/create/remove VMs within an ``OpenNebula`` infrastructure.

AII
===


This section describes AII's OpenNebula hook.

SYNOPSIS
--------


This AII hook generates the required resources and templates to instantiate/create/remove VMs within an OpenNebula infrastructure.


RESOURCES
---------


AII setup
^^^^^^^^^


Set OpenNebula endpoints RPC connector `/etc/aii/opennebula.conf`

It must include at least one RPC endpoint and password.

To connect to a secure https endpoint for example you can set the URL endpoint and CA certificate location:


.. code-block:: perl

     url=https://host.example.com:2633
     ca=/etc/pki/CA/certs/mycabundle.pem


By default ONE AII uses oneadmin user and port 2633.

It is also possible to set a different endpoint for each VM domain or use a fqdn pattern
as example:


.. code-block:: perl

     [rpc]
     password=
     url=https://localhost/RPC2
     ca=/etc/pki/CA/certs/mycabundle.pem
 
     [example.com]
     password=
     user=
 
     [myhosts]
     pattern=myhos\d+.example.com
     password=
     url=http://example.com:2633/RPC2





Public methods
==============



- process_template_aii
 
 Detect and process ``OpenNebula`` ``VM`` templates.
 


- read_one_aii_conf
 
 Reads a config file in ``.ini`` style with a minimal RPC endpoint setup.
 Returns an ``OpenNebula`` instance afterwards.
 


- is_supported_one_version
 
 Detects ``OpenNebula`` version.
 Returns false if <OpenNebula> version is not supported.
 


- get_fqdn
 
 Returns ``fqdn`` of the VM
 


- get_resource_instance
 
 Returns ONE virtual resource instance from ``RPC``
 


- is_timeout
 
 Check if the resource is available
 before our ``$TIMEOUT``
 


- is_one_resource_available
 
 Detects if the resource is already there.
 Returns 1 if resource is already used, undef otherwise.
 


- aii_post_reboot
 
 Performs ``AII`` ``post_reboot``.
 ``ACPID`` service is mandatory for ONE VMs.
 


- aii_configure
 
 Based on Quattor template this method:
 
 
 - Stops running VM if necessary.
 
 
 
 - Creates/updates VM templates.
 
 
 
 - Creates new VM image for each ``$harddisks``.
 
 
 
 - Creates new ``VNET`` ``ARs`` if required.
 
 
 
 - Enables acpid service
 
 
 
 Rename hdx/sdx device disks by vdx to use virtio module
 


- aii_install
 
 Based on Quattor template this method:
 
 
 - Stops current running VM.
 
 
 
 - Instantiates the new VM.
 
 
 


- aii_remove
 
 Performs VM remove wich depending on the booleans.
 
 
 - Stops running VM.
 
 
 
 - Removes VM template.
 
 
 
 - Removes VM image for each ``$harddisks``.
 
 
 
 - Removes vnet ``ARs``.
 
 
 



