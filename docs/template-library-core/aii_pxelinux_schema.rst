#######################
aii\::pxelinux\::schema
#######################

Types
-----

 - **structure_pxelinux_pxe_info**
    - Description: PXE configuration
    - *structure_pxelinux_pxe_info/initrd*
        - Required
        - Type: string
    - *structure_pxelinux_pxe_info/kernel*
        - Required
        - Type: string
    - *structure_pxelinux_pxe_info/ksdevice*
        - Required
        - Type: string
    - *structure_pxelinux_pxe_info/kslocation*
        - Required
        - Type: type_absoluteURI
    - *structure_pxelinux_pxe_info/label*
        - Required
        - Type: string
    - *structure_pxelinux_pxe_info/append*
        - Optional
        - Type: string
    - *structure_pxelinux_pxe_info/rescue*
        - Optional
        - Type: string
    - *structure_pxelinux_pxe_info/livecd*
        - Optional
        - Type: string
    - *structure_pxelinux_pxe_info/firmware*
        - Optional
        - Type: string
    - *structure_pxelinux_pxe_info/setifnames*
        - Optional
        - Type: boolean
    - *structure_pxelinux_pxe_info/updates*
        - Optional
        - Type: type_absoluteURI
    - *structure_pxelinux_pxe_info/ipdev*
        - Description: Get (static) IP details used for ksdevice configuration form this device. For most network configs like bridges and bonds, this is not required.
        - Optional
        - Type: string
