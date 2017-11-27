
### NAME

CAF::ObjectText - Base class for handling text

### SYNOPSIS

Define subclass via
    package SubClass;
    use parent qw(CAF::ObjectText);

    sub _get_text
    {
        my ($self) = @_;
        return "actual text";
    }

And use it via
    my $sc = SubClass->new(log => $self);
    print "$sc"; # stringification

    $sc = SubClass->new(log => $self);
    # return CAF::FileWriter instance (text already added)
    my $fh = $sc->filewriter('/some/path');
    if (!defined($fh)) {
        $self->error("Failed to retrieve filewriter: $sc->{fail}");
        return;
    }
    $fh->close();

### DESCRIPTION

This class simplifies text handling via stringification and produces
a [FileWriter](../CAF/FileWriter.md) instance.

#### Methods

- \_initialize\_textopts

    Handle some common options in the subclass `_initialize` method.

    - `log`

        A [Reporter](../CAF/Reporter.md) object to log to.

    - `eol`

        If `eol` is true, the produced text will be verified that it ends with
        an end-of-line, and if missing, a newline character will be added.
        By default, `eol` is true.

        `eol` set to false will not strip trailing newlines (use `chomp`
        or something similar for that).

    - `usecache`

        If `usecache` is false, the text is always re-produced.
        Default is to cache the produced text (`usecache` is true).

- `_get_text_test`

    Run additional tests before the actual text is produced via `get_text`.
    Returns undef in case of failure, SUCCESS otherwise.

    The method is called in `get_text` before the caching is checked.

    Default implementation does not test anything, always returns SUCCESS.
    This method should be redefined in the subclass.

- `_get_text`

    Produce the actual text in `get_text`
    (or call another method that does so).

    Returns 2 element tuple with first element the resulting text
    (or undef in case of failure). The second element is an error message
    prefix (ideally, real error message is set via the `fail` attribute).

    This method needs to be defined in the subclass.

- `get_text`

    `get_text` produces and returns the text.

    In case of an error, `get_text` returns `undef`
    (no error is logged).
    This is the main difference from the auto-stringification that
    returns an empty string in case of a rendering error.

    By default, the result is cached. To force re-producing the text,
    clear the current cache by passing `1` as first argument
    (or disable caching completely with the option `usecache`
    set to false during the initialisation).

- `filewriter`

    Create and return an open [FileWriter](../CAF/FileWriter.md) instance with
    first argument as the filename. If the `get_text` method fails
    (i.e. returns undef), `undef` is returned.

    The text is added to the filehandle.
    It's up to the consumer to cancel
    and/or close the instance.

    All [FileWriter](../CAF/FileWriter.md) initialisation options are supported
    and passed on. (If no `log` option is provided,
    the one from the current instance is passed).

    Two new options `header` and `footer` are supported
    to respectively prepend and append to the text.

    If `eol` was set during initialisation, the header and footer
    will also be checked for EOL.
    (EOL is still added to the `get_text` if
    `eol` is set during initialisation, even if there is a footer
    defined.)
