######################
functions\::filesystem
######################

Functions
---------

 - num_of_harddisks
    - Description: returns the number of hard disk in the configuration
    - Arguments:
        - none
 - boot_disk
    - Description: returns the disk where grub must be installed
    - Arguments:
        - none
 - lvs_add
    - Description: Adds a list of logical volumes to a volume group. For more details, see https://twiki.cern.ch/twiki/bin/view/FIOgroup/TsiCDBBlockDevices#Proposed_helper_functions
    - Arguments:
        - volume group, list of logical groups to add
 - partitions_add
    - Description: Adds a list of partitions to a disk
    - Arguments:
        - holding device, list of partitions to creatd, optionally id of the extended partition,
 - filesystem_mod
    - Description: modify an existing entry in filesystem list or add it if it doesn't exist yet
    - Arguments:
        - list of structure_filesystem entries. If there is only one entry, a structure_filesystem (dict) may be passed as argument
 - filesystem_del
    - Description: delete one or more filesystem from the filesystem list
    - Arguments:
        - one or a list of mountpoints (string) to remove from filesystem list
