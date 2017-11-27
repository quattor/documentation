
### NAME

Test::Quattor::Doc - Class for unittesting documentation.

### DESCRIPTION

This is a class to trigger documentation testing.
Should be used mainly as follows:

    use Test::Quattor::Doc;
    Test::Quattor::Doc->new()->test();

#### Public methods

- new

    Returns a new object, accepts the following options

    - poddirs

        Array reference of directories to test for podfiles.
        Default dirs are the relative paths `target/lib/perl`
        and `target/doc/pod` (use the exported `@DOC_TEST_PATHS`
        list of defaults or resp. `$DOC_TARGET_PERL` and <$DOC\_TARGET\_POD>)

    - podfiles

        Array reference of podfiles to test (default empty)

    - emptypoddirs

        Array reference of poddirs that must be empty (or non-existing).
        If a directory is in both `poddirs` and `emptypoddirs`,
        if is considered an empty poddir.

    - panpaths

        Array reference of paths that hold pan files to check for annotations.
        Default is `target/pan` (use the exported $DOC\_TARGET\_PAN).

    - panout

        Output path for pan annotations. Default
        target/panannotations (use exported $DOC\_TARGET\_PANOUT).

- pod\_files

    Test all files from `podfiles` and `poddirs`.
    Based on `all_pod_files_ok` from `Test::Pod`.

    Returns array refs of all ok and not ok files.

- pan\_annotations

    Generate annotations, return arrayref with templates that
    have valid annotations and one for templates with invalid annotations.

    TODO: Does not require annotations at all nor validates
    minimal contents.

- test

    Run all tests:
        pod\_files
        pan\_annotations
