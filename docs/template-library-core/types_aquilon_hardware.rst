##########################
types\::aquilon\::hardware
##########################

Types
-----

 - **structure_rack**
    - Description: Rack definition
    - *structure_rack/column*
        - Required
        - Type: string
    - *structure_rack/name*
        - Required
        - Type: string
    - *structure_rack/room*
        - Optional
        - Type: string
    - *structure_rack/row*
        - Required
        - Type: string
 - **structure_sysloc**
    - Description: system location definition For clusters (and thus for virtual machines in the cluster), no attribute is mandatory. The only requirement is that one is defined.
    - *structure_sysloc/building*
        - Optional
        - Type: string
    - *structure_sysloc/campus*
        - Optional
        - Type: string
    - *structure_sysloc/city*
        - Optional
        - Type: string
    - *structure_sysloc/country*
        - Optional
        - Type: string
    - *structure_sysloc/continent*
        - Optional
        - Type: string
    - *structure_sysloc/room*
        - Optional
        - Type: string
    - *structure_sysloc/bunker*
        - Optional
        - Type: string
    - *structure_sysloc/region*
        - Optional
        - Type: string
 - **structure_hardware_aquilon**
    - *structure_hardware_aquilon/rack*
        - Optional
        - Type: structure_rack
    - *structure_hardware_aquilon/sysloc*
        - Optional
        - Type: structure_sysloc
