#######################
aii\::pxelinux\::config
#######################

Variables
---------

 - LPXELINUX
    - Description: Use sys/pxelinux with lpxelinux.0 Tested with pxelinux.0 gpxelinux.0 chain.c32 ldlinux.c32 lpxelinux.0 from SYSLINUX 6.03, should work since 5.10.
 - LPXELINUX_OSINSTALL_PATH
    - Description: Relative path from the AII_OSINSTALL_PATH. defaults to images/pxeboot
 - LPXELINUX_ROOT
    - Description: Base HTTP URL to find vmlinuz and initrd
 - AII_KS_PATH
 - AII_KS_CONFIG_FILE
 - AII_NBP_LABEL
 - AII_NBP_ROOT
 - AII_NBP_INITRD
 - AII_NBP_KERNELPARAMS
