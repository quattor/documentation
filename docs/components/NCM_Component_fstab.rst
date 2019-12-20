
#######################
NCM\::Component\::fstab
#######################


***********
DESCRIPTION
***********


The \ *fstab*\  component manages the mount points in a node. It is able
to manipulate ``/etc/fstab``, and remount filesystems as specified by the
profile. It doesn't perform any dangerous operations, such as
formatting or partitioning. If you need so, use ncm-filesystems in
addition to this component.

It doesn't remove any filesystems specified under
``/software/components/fstab/protected_mounts``.

