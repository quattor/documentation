
### NAME

CAF::Application - Common Application Framework core class

### SYNOPSIS

    package example;
    use strict;
    use warnings;
    use LC::Exception qw (SUCCESS throw_error);
    use parent qw(CAF::Application);

    <extend/overwrite default methods here...>
    # Main loop
    package main;
    use strict;
    use warnings;
    use LC::Exception qw (SUCCESS throw_error);

    use vars ($this_app %SIG);

    unless ($this_app = example->new($0,@ARGV)) {
      throw_error (...);
    }

    $this_app->report("Hello");
    ...

### DESCRIPTION

**CAF::Application** is the core class which provides command line and
configuration file parsing, and general application methods.

Applications can extend or overwrite the default methods.

#### Public methods

- name(): string

    Return the application name (basename)

- version(): string

    Returns the version number as defined in $self->{'VERSION'}, or
    <unknown> if not defined.

- hostname(): string

    Returns the machine's hostname.

- username(): string

    Returns the name of the user.

- option\_exists($opt): boolean

    Returns true if the option exists, false otherwhise. Option can be
    defined either in the application configuration file or on the
    command line (based on `AppConfig` module).

- option($opt): scalar|undef

    Returns the option value coming from the command line and/or
    configuration file. Scalar can be a string, or a reference to a hash
    or an array containing the option's value. option() is a wrapper
    on top of AppConfig->get($opt).

    If the option doesn't exist, returns `undef`, except if the `default`
    argument has been specified: in this case this value is returned but
    the option remains undefined.

- set\_option($opt, $val): SUCCESS

    Defines an option and sets its value. If the option was previously
    defined, its value is overwritten. This is a wrapper over `AppConfig`
    methods to hide the internal implementation of a `CAF::Application`.

    This method always returns SUCCESS.

- show\_usage(): boolean

    Prints the usage message of the command based on options and help text.

- show\_version(): boolean

    prints the version number of the Application.

- app\_options(): ref(array)

    to be overloaded by the application with application specific options.

    This function has to return a reference to an array.
    Every element in the array must be a reference to a hash with the
    following structure:

        NAME    => option name specification in the Getopt::Long(3pm) format
                   "name|altname1|altname2|..[argument_type]"
        DEFAULT => [optional] default value (string). If not specified: undef
        HELP    => help text (string)

    example:

        push(@array, {NAME =>'M|myoption=s' ,
                      DEFAULT=>'defaultvalue',
                      HELP=>'do somewhat on something'});

        return \@array;

    see also \_app\_default\_options()

#### Private methods

- \_initialize

    Initialize the Application.

    Arguments

    - `$command`

        Name of the script/command/... (typically `$0`).

    - Remaining arguments `@argv`

        Typically this is the perl builtin variable `@ARGV`,
        but can be any array of options/arguments,
        or a single arrayref (in which case all elements
        of the arrayref are handled as options/arguments).

        Any arguments that are not handled by the options,
        can be retrieved either via `@ARGV` or by passing
        an arrayref holding the options/arguments.
        In these 2 cases, the contents is modified,
        removing all handled options, leaving the
        non-option arguments in place.
        (In particular, using a regular array
        will leave the original array unmodified).

- \_app\_default\_options

    This method specifies a number of default options, with the
    same format as app\_options. The options are:

        debug <debuglevel> : sets debug level (1 to 5)
        help               : prints out help message
        quiet              : no output
        verbose            : verbose output
        version            : print out version number & exit

    The 'noaction', 'cfgfile' and 'logfile' options are not enabled
    by default but recognized (they have to be added to the application
    specific code - see the 'example' file):

        noaction           : execute no operations
        cfgfile <string>  : use configuration file <string>
        logfile  <string>  : use log file <string>

- \_add\_options

    add options coming from \_app\_default\_options() and app\_options()
