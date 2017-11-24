
### NAME

CAF::Path - check that things are really the way we expect them to be

### DESCRIPTION

Simplify common file and directory related operations e.g.

- directory creation
- cleanup
- (mockable) file/directory tests

The class is based on **LC::Check** with following major difference

- `CAF::Object::NoAction` support builtin (and `keeps_state` option to override it).
- support [Reporter](../CAF/Reporter.md) (incl. `CAF::History`)
- raised exceptions are catched, methods return SUCCESS on succes,
undef on failure and store the error message in the `fail` attribute.
- available as class-methods
- return values
    - undef: failure occured
    - SUCCESS: nothing changed (boolean true)
    - CHANGED: something changed (boolean true).

#### Functions

- mkcafpath

    Returns an instance of [Object](../CAF/Object.md) and `CAF::Path`.
    This instance is a simple way to use `CAF::Path` when
    subclassing is not possible. Allowed options are
    `<log =` $logger>> and `<NoAction =` $noaction>>.

    This function is not exported, to be used as e.g.
        use CAF::Path;
        ...
        my $cafpath = CAF::Path::mkcafpath(log => $logger);
        if(! defined($cafpath->directory($name)) {
            $logger->error("Failed to make directory $name: $cafpath->{fail}");
        };

#### Methods

- \_get\_noaction

    Return NoAction setting:

    - Return 0 is `keeps_state` is true

        Any other value of `keeps_state` is ignored. (In particular,
        you cannot use `keeps_state` to enable NoAction).

    - Return value of `CAF::Object::NoAction` otherwise.

    Supports an optional `msg` that is prefixed to reporter.

- \_reset\_exception\_fail

    Reset previous exceptions and/or fail attribute.

- \_function\_catch

    Execute function reference `funcref` with arrayref `$args` and hashref `$opts`.

    Method resets/ignores any existing errors and fail attribute, and catches any exception thrown.
    No error is reported, it returns undef in this case and the fail attribute is set.

- \_safe\_eval

    Run function reference `funcref` with arrayref `argsref` and hashref `optsref`.

    Return and set fail attribute with `failmsg` on die or an error (`undef` returned
    by `funcref`), or print (at verbose level) `msg` on success (respectively $@ and
    stringified result are appended). Note that `_safe_eval` doesn't work with functions
    that don't return a defined value when they succeed.

    Resets previous exceptions and/or fail attribute

- LC\_Check

    Execute function `<LC::Check::<function`>> with arrayref `$args` and hashref `$opts`.

    `CAF::Object::NoAction` is added to the options, unless `keeps_state` is set.

    The function is executed with `_function_catch`.

- \_untaint\_path

    Untaint the `path` argument.

    Returns undef on failure and sets the fail attribute with `msg`

- directory\_exists

    Test if `directory` exists and is a directory.

    This is basically the perl builtin `-d`,
    wrapped in a method to allow unittesting.

    If  `directory` is a symlink, the symlink target
    is tested. If the symlink is broken (no target),
    `directory_exists` returns false.

- file\_exists

    Test if `filename` exists and is a file.

    This is basically the perl builtin `-f`,
    wrapped in a method to allow unittesting.

    If  `filename` is a symlink, the symlink target
    is tested. If the symlink is broken (no target),
    `file_exists` returns false.

- any\_exists

    Test if `path` exists.

    This is basically the perl builtin `-e || -l`,
    wrapped in a method to allow unittesting.

    A broken symlink (symlink whose target doesn't
    exist) exists: `any_exists` returns true.

- is\_symlink

    Test if `path` is a symlink.

    Returns true as long as `path` is a symlink, including when the
    symlink target doesn't exist.

- cleanup

    cleanup removes `dest` with backup support.

    (Works like `LC::Check::_unlink`, but has directory support
    and no error throwing).

    Returns CHANGED is something was cleaned-up, SUCCESS if nothing was done
    and undef on failure (and sets the fail attribute).

    The <backup> is a suffix for `dest`.

    If backup is undefined, use `backup` attribute.
    (Pass an empty string to disable backup with `backup` attribute defined)
    Any previous backup is `cleanup`ed (without backup).
    (Aside from the `backup` attribute, this is the same as `LC::Check::_unlink`
    (and thus also `CAF::File*`)).

    Additional options

    - keeps\_state: boolean passed to `_get_noaction`.

- directory

    Make sure a directory exists with proper options.

    If the directory does not exists (or the `temp` option is set),
    it is created (including the parent directories as needed),
    and uses `LC::Check::directory` via `LC_Check`.

    Returns CHANGED if a change was made, SUCCESS if no changes were made
    and undef in case of failure (and the `fail` attribute is set).

    The return value in absence of failure is a dualvar with integer value
    SUCCESS/CHANGED, and the directory as string value
    (in particular relevant for temporary directories).

    Additional options

    - owner/group/mode/mtime : options for `CAF::Path::status`
    - temp

        A boolean if true will create a a temporary directory using
        **File::Temp::tempdir**.

        The directory name is the template to use (any trailing
        `X` characters will be replaced with random characters by `tempdir`;
        and the directory name will be padded up to at least 4 `X`).

        The `CLEANUP` option is also set (an removal
        attempt (incl. any files and/or subdirectries)
        will be made at the end of the program).

    - keeps\_state: boolean passed to `_get_noaction`.

- \_make\_link

    This method is mainly a wrapper over `LC::Check::link`
    returning the standard `CAF::Path` return values. Every option
    supported by `LC::Check::link` is supported. `NoAction`
    flag is handled by `LC::Check::link` and `keeps_state` option
    is honored (overrides `NoAction` if true). One important
    difference is the order of the arguments: `CAF::Path:_make_link`
    and the methods based on it are following the Perl `symlink`
    (and `ln` command) argument order.

    This is an internal method, not supposed to be called directly.
    Either call [symlink](../components/symlink.md) or `hardlink` public methods instead.

- hardlink

    Create a hardlink `link_path` whose target is `target`.

    On failure, returns undef and sets the fail attribute.
    If `link_path` exists and is a file, it is updated.
    `target` must exist (`check` flag available in symlink()
    is ignored for hardlinks) and it must reside in the same
    filesystem as `link_path`. If `target_path` is a
    relative path, it is interpreted from the current directory.
    `link_name` parent directory is created if it doesn't exist.

    Returns SUCCESS on sucess if the hardlink already existed
    with the same target, CHANGED if the hardlink was created
    or updated, undef otherwise.

    This method relies on `_make_link` method to do the real work,
    after enforcing the option saying that it is a hardlink.

- symlink

    Create a symlink `link_path` whose target is `target`.

    Returns undef and sets the fail attribute if `link_path`
    already exists and is not a symlink, except if this is a file
    and option `force` is defined and true. If `link_path` exists
    and is a symlink, it is updated. By default, the target is not
    required to exist. If you want to ensure that it exists,
    define option `check` to true. Both `link_path` and `target`
    can be relative paths: `link_path` is interpreted as relatif
    to the current directory and `target` is kept relative.
    `link_path` parent directory is created if it doesn't exist.

    Returns SUCCESS on sucess if the symlink already existed
    with the same target, CHANGED if the symlink was created
    or updated, undef otherwise.

    This method relies on `_make_link` method to do the real work,
    after enforcing the option saying that it is a symlink.

- has\_hardlinks

    Method that returns the number of hardlinks for `file`. The number of
    hardlinks is the number of entries referring to the inodes minus 1. If
    `file` has no hardlink, the return value is 0. If `file` is not a file,
    the return value is `undef`.

- is\_hardlink

    This method returns SUCCESS if `path1` and `path2` refer to the same file (inode).
    It returns 0 if `path1` and `path2` both exist but are different files or are the same path
    and `undef` if one of the paths doesn't exist or is not a file.

    Note: the result returned will be identical whatever is the order of `path1` and `path2`
    arguments.

- status

    Set the path stat options: `owner`, `group`, `mode` and/or `mtime`.

    This is a wrapper around `LC::Check::status`
    and executed with `LC_Check`.

    Returns CHANGED if a change was made, SUCCESS if no changes were made
    and undef in case of failure (and the `fail` attribute is set).

    Additional options

    - keeps\_state: boolean passed to `_get_noaction`.

- move

    Move/rename `src` to `dest`.

    The final goal is to make sure `src` does not exist anymore,
    not that `dest` exists after move (in particular, if `src`
    does not exist to start with, success is immediately returned,
    and no backup of `dest` is created).

    The <backup> is a suffix for the cleanup of `dest`
    (and passed to `cleanup` method).

    (The basedir of `dest` is created using `directory` method.)

    Additional options

    - keeps\_state: boolean passed to `_get_noaction`.
