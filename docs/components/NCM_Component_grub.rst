
######################
NCM\::Component\::grub
######################


****
NAME
****


The \ *grub*\  component manages the grub configuration.


***********
DESCRIPTION
***********


The \ *grub*\  component manages the configuration of grub.

Most of the configuration is handled via the ``grubby`` tool
(which supports grub2).

Some configuration like serial console settings and password
however is done by modifying the grub configfile
directly, which might not be safe under grub2.


*********
RESOURCES
*********


Besides ``/software/component/grub``, following resources are used:


- ``/system/kernel/version`` for setting the default kernel



- ``/hardware/console/serial`` for serial console configuration




********
EXAMPLES
********



- A standard SL4 kernel with initrd image to be loaded.


 .. code-block:: perl

    "/software/components/grub/kernels/0" =
          nlist("kernelpath", "/vmlinuz-2.6.9-22.0.1.EL",
                "kernelargs", "ro root=LABEL=/",
                "title", "Scientific Linux 4.2 / 2.6.9",
                "initrd", "/initrd-2.6.9-22.0.1.EL.img"
    );


 This configuration produces the following entry in grub.conf (via grubby):


 .. code-block:: perl

    title Scientific Linux 4.2 / 2.6.9
          kernel `/vmlinuz`-2.6.9-22.0.1.EL ro root=LABEL=/
          initrd `/initrd`-2.6.9-22.0.1.EL.img




- A Xen 3 hypervisor with Linux 2.6 domain 0 kernel and initrd (via grubby).


 .. code-block:: perl

    "/software/components/grub/kernels/1" =
          nlist("multiboot", "/xen-3.0.2-2.gz",
                "mbargs", "dom0_mem=400000",
                "title", "Xen 3 / XenLinux 2.6.16",
                "kernelpath", "/vmlinuz-2.6.16-xen3_86.1_rhel4.1",
                "kernelargs", "max_loop=128 root=/dev/hda2 ro",
                "initrd", "/initrd-2.6.16-xen3_86.1_rhel4.1"
    );


 Produces the following entry in grub.conf:


 .. code-block:: perl

    title Xen 3 / XenLinux 2.6.16
          kernel `/xen`-3.0.2-2.gz dom0_mem=400000 addthis
          module `/vmlinuz`-2.6.16-xen3_86.1_rhel4.1 max_loop=128 root=/dev/hda2 ro
          module `/initrd`-2.6.16-xen3_86.1_rhel4.1




Methods
=======



- convert_grubby_arguments

 Given ``args`` string or hashref, update ``arguments`` hashref
 with add/remove hashrefs. Optional serial console kernel commandline option ``cons``

 If ``args`` is a string, arguments prefixed with '-' are added to the remove hashref.

 Returns ``arguments`` hashref with add and remove hashrefs.

 If track is false, the values of add and remove hashrefs are the last encountered value.
 If track is true, the values of add and remove hashrefs are arraysrefs with all encountered values.



- assemble_grubby_options

 Given ``arguments`` hashref, return the add and remove option arrayrrefs.



- grubby_arguments_options

 Given arguments hashref ``args``, convert into grubby commandline options
 to add and/or remove the arguments.
 If ``multiboot`` is true, generate multiboot commandline options

 Returns a list of options.



- password

 Configure the grub password by editing the grub conf via filehandle
 ``grub_fh`` (a ``CAF::FileEditor`` instance,
 which is not closed in this method).

 Returns SUCCESS on succes, undef otherwise.



- serial_console

 Configure the grub serial console settings (``ttyS`` devices only)
 by editing the grub conf via filehandle ``grub_fh``
 (a ``CAF::FileEditor`` instance, which is not closed in this method).

 Returns undef on failure, the console kernel commandline option
 (or empty string if none is to be configured) on success.



- main_section_offset

 Given a grub config filehandle (a ``CAF::FileEditor`` instance),
 return the startposition of the main section
 i.e. after the header comments (if any).



- grub_conf

 Edit grub configfile and
 return serial console kernel commandline option (if any).



- grubby

 Run ``grubby`` with arraref ``args`` via ``CAF::Proces`` using the
 ``output`` method and return the output.

 Has following options


 - proc: return new ``CAF::Process`` instance with ``args`` (i.e. without execute/output)



 - success: run execute and return 1 on success, 0 on failure



 - keeps_state: pass keeps_state flag





- current_default

 Return current full path of current default kernel.



- set_default

 Set default kernel to ``new`` kernelpath and verify by (re)checking the default kernel.

 Returns success on success; on failure, return either


 - undef: setting default kernel returned non-zero exitcode



 - 0: setting default was succesful, but new default kernel is not expected kernel



 No errors are reported.



- configure_default

 Configure the new default kernel to be ``new``.
 If this fails and ``mbnew`` exists, try to set ``mbnew`` as default.

 If neither ``new`` nor ``mbnew`` are successful,
 report an error and revert to ``original``.



- kernel

 Configure boot entry using ``kernel`` hashref, the kernel ``prefix``
 and optional serial console kernel commandline option ``cons``.

 Any serial console settings in the ``kernelargs`` attribute
 is replaced by ``cons`` (when defined).



- get_info

 Return info for default kernel as an arrayref of hashref

 Same kernel can have multiple entries.



- current_arguments

 Get the current arguments. Return current arguments as string and as parsed hasref

 ``track`` option is passed to ``convert_grubby_arguments``.



- sanitize_arguments

 Sanitize the current arguments



- default_options

 Configure kernel commandline options of default kernel



- pxeboot

 Set pxeboot as first bootorder.
 Returns SUCCESS on success, undef otherwise.

 Currently only supported on UEFI systems using ``efibootmgr``. On other systems,
 SUCCESS is also returned (but nothing is done).



- Configure

 Updates the grub.conf configuration file using grubby according to a
 list of kernels described in the profile.

 Sets the default kernel to that specified in ``/system/kernel/version``.

 Supports


 - serial console configuration specified in ``/hardware/console/serial``.



 - multiboot loaders (most commonly used for configuration of Xen systems).



 Returns error in case of failure.




