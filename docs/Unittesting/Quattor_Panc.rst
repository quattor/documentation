
##############
Quattor\::Panc
##############


***********
DESCRIPTION
***********


Module to compile profiles using panc

set_panc_options
================


Set additional panc commandline options.
Use the long option name, the preceding '--' is added.
If no value is expected (e.g. '--debug') pass 'undef' as value.


reset_panc_options
==================


Reset the panc commandline options.

head2 get_panc_options

Returns the hash reference to the additional pancoptions.


set_panc_includepath
====================


Set the inlcudedirs option to the directories passed.
If undef is passed, remove the 'includepath' option.


get_panc_includepath
====================


Return an array reference with the 'includepath' directories.


is_object_template
==================


Given profile name (and optional resourcesdir for relative profile filename),
test if the profile is a valid object template.


Compile pan object template into JSON profile
=============================================


Compile the pan ``profile`` (file '``profile``.pan' in ``resourcesdir``)
and create the profile in ``outputdir``.

If ``croak_on_error`` is true (or undef), the method croaks on compilation failure.
If false, it will return the exitcode.


panc_annotations
================


Generate the pan annotations from ``basedir`` in ``outputdir`` for ``profiles``.


process
=======


Sort-of private method to use ``CAF::Process`` bypassing the mocking of ``CAF::Process``.

Arrayhash ``$cmd`` for the command, ``$message`` for a message to print.

Options


- croak_on_error: ``croak`` on error



- srcdir: srcdir to return to after actual command is executed.



- output: return arrayref with exitcode and output (stdout combined with stderr)




