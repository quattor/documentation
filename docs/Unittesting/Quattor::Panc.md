
### DESCRIPTION

Module to compile profiles using panc

#### set\_panc\_options

Set additional panc commandline options.
Use the long option name, the preceding '--' is added.
If no value is expected (e.g. '--debug') pass 'undef' as value.

#### reset\_panc\_options

Reset the panc commandline options.

head2 get\_panc\_options

Returns the hash reference to the additional pancoptions.

#### set\_panc\_includepath

Set the inlcudedirs option to the directories passed.
If undef is passed, remove the 'includepath' option.

#### get\_panc\_includepath

Return an array reference with the 'includepath' directories.

#### is\_object\_template

Given profile name (and optional resourcesdir for relative profile filename),
test if the profile is a valid object template.

#### Compile pan object template into JSON profile

Compile the pan [profile](../components/profile.md) (file '`profile`.pan' in `resourcesdir`)
and create the profile in `outputdir`.

If `croak_on_error` is true (or undef), the method croaks on compilation failure.
If false, it will return the exitcode.

#### panc\_annotations

Generate the pan annotations from `basedir` in `outputdir` for `profiles`.

#### process

Sort-of private method to use [Process](../CAF/Process.md) bypassing the mocking of [Process](../CAF/Process.md).

Arrayhash `$cmd` for the command, `$message` for a message to print.

Options

- croak\_on\_error: `croak` on error
- srcdir: srcdir to return to after actual command is executed.
- output: return arrayref with exitcode and output (stdout combined with stderr)
