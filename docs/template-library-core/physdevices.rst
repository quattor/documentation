###########
physdevices
###########

Types
-----

 - **structure_raidport**
    - *structure_raidport/capacity*
        - Required
        - Type: long
    - *structure_raidport/interface*
        - Required
        - Type: string
    - *structure_raidport/boot*
        - Optional
        - Type: boolean
    - *structure_raidport/part_prefix*
        - Required
        - Type: string
 - **structure_raid**
    - Description: Structure modelling a RAID controller
    - *structure_raid/bbu*
        - Optional
        - Type: boolean
    - *structure_raid/numberports*
        - Required
        - Type: long
        - Range: 1..
    - *structure_raid/cache*
        - Optional
        - Type: long
    - *structure_raid/ports*
        - Required
        - Type: structure_raidport
