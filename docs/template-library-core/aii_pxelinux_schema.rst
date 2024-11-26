#######################
aii\::pxelinux\::schema
#######################

Types
-----

 - **structure_pxelinux_pxe_info**
    - Description: PXE configuration
    - *structure_pxelinux_pxe_info/kernel*
        - Description: Kernel path (string in exact syntax). If this contains a '@pattern@' substring, the kernel path is generated based on the (first) enabled SPMA repository with name matching this glob pattern (without the '@').
        - Required
        - Type: string
    - *structure_pxelinux_pxe_info/initrd*
        - Description: Initrd path (string in exact syntax). If this contains a '@pattern@' substring, the initrd path is generated based on the (first) enabled SPMA repository with name matching this glob pattern (without the '@').
        - Required
        - Type: string
    - *structure_pxelinux_pxe_info/efi_name_lookup*
        - Description: try to resolve the hostname (when relevant) for EFI kernel and/or initrd; to use the ip instead of the hostname
        - Optional
        - Type: boolean
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
