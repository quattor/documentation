
########################
NCM\::Component\::autofs
########################


****
NAME
****


``ncm-autofs``: NCM component to manage autofs configuration.


***********
DESCRIPTION
***********


The \ *autofs*\  component manages autofs master map and generated maps. It allows
both exclusive management by the component or preservation of local changes.


********
EXAMPLES
********


Scenario 1 : Configure a NFS mountpoint
=======================================


We will mount the NFS filesystem nfsserv.example.org: ``/data`` under ``/tmp_mnt/nfsdata``


.. code-block:: perl

    prefix '/software/components/autofs/maps/data';
    'entries/nfsdata/location' = 'nfsserv.example.org:/data';
    'mapname' = '/etc/auto.nfsdata';
    'mountpoint' = '/tmp_mnt';
    'options' = 'rw,noatime,hard';



Scenario 2 : Configuration with dict() usage
============================================



.. code-block:: perl

     prefix '/software/components/autofs';
     'preserveMaster' = false;
 
     prefix '/software/components/autofs/maps/misc';
     'enabled' = true;
     'preserve' = false;
     'mapname' = '/etc/auto.misc';
     'type' = 'file';
     'mountpoint' = '/misc';
     'entries' = dict(
         'kickstart', dict(
             'location', 'misc.example.com:/misc'
         )
     );
 
     prefix '/software/components/autofs/maps/garden';
     'enabled' = true;
     'preserve' = false;
     'mapname' = '/etc/auto.garden';
     'type' = 'file';
     'options' = '';
     'mountpoint' = '/home/garden';
     'entries' = dict(
         escape('*'), dict(
             'options', '-rw,intr,rsize=8192,wsize=8192,actimeo=60,addr=10.21.12.10',
             'location', 'crown-city.albion.net:/home/garden/&'
         )
     );



