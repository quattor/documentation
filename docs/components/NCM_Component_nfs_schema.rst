##############################
NCM\::Component\::nfs - schema
##############################

Types
-----

 - **/software/components/nfs/structure_nfs_exports**
    - */software/components/nfs/structure_nfs_exports/path*
        - Required
        - Type: string
    - */software/components/nfs/structure_nfs_exports/hosts*
        - Required
        - Type: string
 - **/software/components/nfs/structure_nfs_mounts**
    - */software/components/nfs/structure_nfs_mounts/device*
        - Required
        - Type: string
    - */software/components/nfs/structure_nfs_mounts/mountpoint*
        - Required
        - Type: string
    - */software/components/nfs/structure_nfs_mounts/fstype*
        - Required
        - Type: string
    - */software/components/nfs/structure_nfs_mounts/options*
        - Optional
        - Type: string
    - */software/components/nfs/structure_nfs_mounts/freq*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/nfs/structure_nfs_mounts/passno*
        - Optional
        - Type: long
        - Range: 0..
 - **/software/components/nfs/nfs_component**
    - */software/components/nfs/nfs_component/server*
        - Description: Configure a NFS server. In particular relevant for missing exports attribute. If true, missing exports forces an empty exports file and a NFS service reload. If false, missing exports has no effect.
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/nfs/nfs_component/exports*
        - Description: This is a list of dicts with "path" giving the export path and "hosts" being a dict of host/option entries where the key is the escaped host name and the value the export options(e.g. for "nfsclient.example.org(rw)", key will be escape("nfsclient.example.org") and value will be 'rw'. Note that the values in "hosts" may NOT contain embedded spaces and should not contain the enclosing '()'. This restriction is not checked in the schema! If a path is listed more than once, then the last entry will be used to generate the exports file.
        - Optional
        - Type: structure_nfs_exports
    - */software/components/nfs/nfs_component/mounts*
        - Description: This is a list of dicts with mandatory values for "device", "mountpoint", and "fstype". The named lists may contain values for "options", "freq", and "passno". the defaults being "defaults", 0, and 0, respectively. If a device is listed multiple times, then the last entry will be used to generate a line in the /etc/fstab file. Entries are added in the order given in the list AFTER preexisting entries in the fstab file. If the mounts change, then the component will attempt to unmount any mounts which are removed and mount any new ones. If the options change, then the volume will be remounted. If the list is empty, all supported mounts in fstab will be removed. If you don't want ncm-nfs to modify /etc/fstab, do not set the mounts attribute at all.
        - Optional
        - Type: structure_nfs_mounts
