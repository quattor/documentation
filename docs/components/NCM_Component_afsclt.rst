
########################
NCM\::Component\::afsclt
########################


****
NAME
****


NCM::afsclt - NCM AFS client configuration component


********
SYNOPSIS
********



- Configure()
 
 Configure the cell, the AFS cacheinfo file and the afsd daemon.
 



*********
RESOURCES
*********



- ``/software/components/afsclt/afsd_args`` : nlist (optional)
 
 various command-line options for the afsd daemon
 


- ``/software/components/afsclt/afs_mount`` : string (optional)
 
 AFS mount point. If not defined, ``/afs`` is used.
 


- ``/software/components/afsclt/cachemount`` : string (optional)
 
 AFS cache mount point. No default.
 


- ``/software/components/afsclt/cachesize`` : string (optional)
 
 desired AFS cache size on disk, in 1K blocks, or ``AUTOMATIC``. The running AFS cache
 will get adjusted online, and ``$afs_cacheinfo`` will be changed if
 required. Please note that an available (mounted) AFS cache partition
 has precedence over this value, i.e. you cannot force a lower usage of
 the cache partition. For Linux machines, a cache partition will use
 ``CACHESIZE=AUTOMATIC``, for other OSes, a hardcoded fill rate of 85% is
 used.
 


- ``/software/components/afsclt/cellservdb`` : string (optional)
 
 A regularly-updated AFS CellServDB URL or filename (e.g. from AFS)
 that this component will copy to local disk. The local AFS client will
 get notified of any additions or changes within a cell.
 


- ``/software/components/afsclt/enabled`` : ``yes`` or ``no`` (required)
 
 Whether the AFS client should be enabled or not. No default.
 


- ``/software/components/afsclt/settime`` : boolean (optional)
 
 make AFS client set the system time or not.
 


- ``/software/components/afsclt/thiscell`` : string (required)
 
 local AFS cell for this machine. No default.
 


- ``/software/components/afsclt/thesecells`` : list of string (optional)
 
 List of AFS cells to authenticate to. No default.
 


