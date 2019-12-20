
#######
Quattor
#######


********
SYNOPSIS
********



.. code-block:: perl

     use Test::Quattor qw(test_profile1 test_profile2...);



***********
DESCRIPTION
***********


``Test::Quattor``

Module preparing the environment for testing Quattor code.


*******
LOADING
*******


When loading this module it will compile any profiles given as arguments. So,


.. code-block:: perl

     use Test::Quattor qw(foo);


will trigger a compilation of ``src/test/resources/foo.pan`` and the
creation of a binary cache for it. The compiled profile will be stored
as ``target/test/profiles/foo.json``, while the cache will be stored in
under ``target/test/profiles/foo/``.

This binary cache may be converted in an
``EDG::WP4::CCM::CacheManager::Configuration`` object using the
``get_config_for_profile`` function.


***********************
INTERNAL INFRASTRUCTURE
***********************


Module variables
================


This module provides backup methods for several ``CAF`` modules. They
will prevent tests from actually modifying the state of the system,
while allowing an NCM component to follow a realistic execution path.

These backups record what files are being written, what commands are
being run, and allow for inspection by a test.

This is done with several functions, see \ **Redefined functions**\  below,
that control the following variables:


* QUATTOR_TEST_LOG_DEBUGLEVEL
 
 If the environment variable QUATTOR_TEST_LOG_DEBUGLEVEL is set, the unittests
 will run with this debuglevel (0-5). Otherwise the default loglevel is 'verbose'.
 
 To actually see the verbose or debug output, you need to run prove with verbose flag
 (e.g. by passing ``-Dprove.args=-v`` or by setting ``-v`` in the ``<~/.proverc``>).
 


* ``$log_cmd``
 
 A boolean to enable logging of each command that is run via CAF::Process.
 Can also be set via the QUATTOR_TEST_LOG_CMD environment variable.
 


* ``$log_cmd_missing``
 
 A boolean to log each cmd that has output mocked but has no output set.
 Can also be set via the QUATTOR_TEST_LOG_CMD_MISSING environment variable.
 


* ``%files_contents``
 
 Contents of a file after it is closed. The keys of this hash are the
 absolute paths to the files.
 
 This hash is a global variable whose contents can be checked in a
 test, if necessary. But if you want to set the file content
 before using the ``CAF::Path`` methods (for example, using
 ``set_file_contents``), it is preferable to use ``%desired_file_contents``.
 


* ``%commands_run``
 
 CAF::Process objects being associated to a command execution.
 


* ``%commands_status``
 
 Desired exit status for a command. If the command is not present here,
 it is assumed to succeed.
 


* ``%desired_outputs``
 
 When we know the component will call ``CAF::Process::output`` and
 friends, we prepare here an output that the component will have to
 deal with.
 


* ``%desired_err``
 
 When the component may analyse the standard error of a component, we
 supply it through this hash.
 


* ``%desired_file_contents``
 
 Initial contents for a file that should be "edited". The content of this hash
 (keys are the absolute path names) is managed/updated by all the ``CAF::FileWriter``
 methods. It is preferable to use it rather than ``%files_contents``, if you don't need
 to access its contents directly from another module (``CAF::FileWriter`` methods give
 access to its contents in fact).
 


* ``@command_history``
 
 CAF::Process commands that were run.
 


* ``caf_path``
 
 A hashref with ``CAF::Path`` methods and arrayref of reference of used arguments
 


* ``NoAction``
 
 Set ``Test::Quattor::NoAction`` to override ``CAF::Object::NoAction``
 in any of the mocked ``Test::Quattor`` methods (where relevant, e.g.
 mocked FileWriter and FileEditor).
 
 E.g. if you want to run tests with ``CAF::Object::NoAction`` not set
 (to test the behaviour of regular ``CAF::Object::NoAction``).
 
 Default is 1.
 


* ``%immutable``
 
 The content of this hash (keys are the absolute path names) indicates
 if paths (files, directories, ...) are immutable (or not).
 Any modification to an immutable path will result in an error.
 
 You can add paths using the ``set_immutable`` function.
 


* ``%status``
 
 The content of this hash (keys are the absolute path names) indicates
 current ``CAF::Path::status`` (``mode``, ``mtime``, ``owner`` and/or ``group``).
 
 You can add paths using the ``set_status`` function.
 



Redefined functions
===================


In order to achieve this, the following functions are redefined
automatically:


- ``CAF::Process::{run,execute,output,trun,toutput}``
 
 Prevent any command from being executed.
 


- ``CAF::FileWriter::open``
 
 Overriding this function allows us to inspect its contents after the
 unit under tests has released it.
 


- ``CAF::FileWriter::close``
 
 Overriding this function to force noaction and update
 mocked ``%desired_file_contents``.
 


- ``CAF::FileWriter::_close``
 
 Mock-only method to make the FileWriter instance not opened
 (in `IO::String <http://search.cpan.org/search?query=IO%3a%3aString&mode=module>`_ sense).
 
 Required for cleanup of filehandles left by eg immutable paths.
 


- ``CAF::FileWriter::_read_contents``
 
 Used to get the original content (for ``<CAF::FileWriter-``close>>) and/or source
 (for ``<CAF::FileEditor-``new>>) from the ``%desired_file_contents``.
 


- ``CAF::FileEditor::_is_valid_file``
 
 Mock using ``is_file`` function.
 


- ``CAF::FileEditor::_is_reference_newer``
 
 Mock using ``is_file`` function (but no support for pipes or
 age test).
 


- ``CAF::FileReader::_is_valid_file``
 
 Mock using ``is_file`` function (but no support for pipes).
 


- ``CAF::Reporter::debug``
 
 Checks that each debug() call starts with a debuglevel between 0 and 5.
 


- ``CAF::Reporter::debug``
 
 Checks that each debug() call starts with a debuglevel between 0 and 5.
 


- ``IO::String::close``
 
 Prevents the buffers from being released when explicitly closing a file.
 


- ``CAF::Path::file_exists``
 
 Return the mocked ``is_file``
 


- ``CAF::Path::directory_exists``
 
 Return the mocked ``is_directory``
 


- ``CAF::Path::any_exists``
 
 Return the mocked ``is_any``
 


- is_symlink
 
 Test if given ``path`` is a mocked symlink
 


- has_hardlinks
 
 Test if given ``path`` is a mocked hardlink
 
 Note that it is not a perfect replacement for the c<CAF::Path> ``has_hardlinks`` because
 the current implementation of mocked hardlinks does not allow to mimic multiple references
 to an inode. The differences are : the link used at creation time must be queried, not the
 target (where in a real hardlink target and link are undistinguishable); if the path is
 a hardlink the number of references for the inode is always 1.
 


- is_hardlink
 
 Test if ``path1`` and ``path2`` are hardlinked
 


- _make_link
 
 Add a mocked ``_make_link``.
 
 This mocked method implements most of the checks done in ``LC::Check::link``, the function
 doing the real work in ``_make_link``, and returns the same values as ``CAF::Path`` ``_make_link``.
 See ``CAF::Path`` comments for details.
 
 Internally, this mocked symlink/hardlink support uses the file contents to track that a path
 is a symlink or hardlink. Thus, in addition to the symlink() and hardlink() methods, a link
 can be created with ``set_file_contents($filename, $Test::Quattor::SYMLINK)`` for a symlink
 and ``set_file_contents($filename, $Test::Quattor::HARDLINK)`` for a hardlink.
 


- ``CAF::Path::directory``
 
 Return directory name unless mocked ``make_directory`` or mocked ``LC_Check`` fail.
 
 (The ``temp`` is ignored wrt creating the directory name).
 


- ``CAF::Path::LC_Check``
 
 Store args in ``caf_path`` using ``add_caf_path``.
 


- ``CAF::Path::cleanup``
 
 ``remove_any`` and store args in ``caf_path`` using ``add_caf_path``.
 


- ``CAF::Path::move``
 
 ``remove_any`` and store args in ``caf_path`` using ``add_caf_path``.
 


- ``CAF::Path::status``
 
 Set and compare status.
 


- ``CAF::Path::_listdir``
 
 Mock underlying _listdir method that does the actual opendir/readdir/closedir.
 
 Has 2 args, one directory and one test function. The is no validation
 of any kind. Do not use this method directly, use ``listdir`` instead.
 




**************************
FUNCTIONS FOR EXTERNAL USE
**************************


The following functions are exported by default:


- ``get_file``
 
 Returns the object that has manipulated ``$filename``
 


- ``set_file_contents``
 
 For file ``$filename``, sets the initial ``$contents`` the component should see.
 It also sets the default ``CAF::FileWriter`` permissions (``mode`` 644).
 
 Returns the contents on success, undef otherwise.
 


- ``get_file_contents``
 
 For file ``$filename``, returns the contents on success, undef otherwise.
 


- ``get_command``
 
 Returns all the information recorded about the execution of ``$cmd``,
 if it has been executed. This is a hash reference in which the
 ``object`` element is the ``CAF::Process`` object itself, and the
 ``method`` element is the function that executed the command.
 


- ``set_command_status``
 
 Sets the "exit status" we'll report for a given command.
 


- ``set_desired_output``
 
 Sets the standard output we'll return when the caller issues ``output``
 on this command
 


- ``set_desired_err``
 
 Sets the standard error we'll receive when the caller issues
 ``execute`` on this command.
 


- ``command_history_reset``
 
 Reset the command history to empty list.
 


- ``command_history_ok``
 
 Given an arrayref of ``required_commands``,
 it checks the ``@command_history`` if all commands were
 called in the given order (it allows for other commands to exist inbetween).
 The commands are interpreted as regular expressions.
 
 E.g. if ``@command_history`` is (x1, x2, x3) then
 ``command_history_ok([x1,X3])`` returns 1
 (Both x1 and x3 were called and in that order,
 the fact that x2 was also called but not checked is allowed.).
 ``command_history_ok([x3,x2])`` returns 0 (wrong order),
 ``command_history_ok([x1,x4])`` returns 0 (no x4 command).
 
 A second arrayref of ``forbidden_commands`` can be given,
 and the ``@command_history`` is then first checked that
 none of those commands occured.
 If you only want to check the non-occurence of commands,
 pass an undef as the first argument
 (and not an empty arrayref).
 


- ``set_service_variant``
 
 Sets the ``CAF::Service`` variant to the one given in the command line:
 
 
 * ``linux_sysv``
  
  Linux SysV, e.g, ``/sbin/service foo start``
  
 
 
 * ``linux_systemd``
  
  Linux, Systemd variant.
  
 
 
 * ``solaris``
  
  Solaris and SMF variant.
  
 
 
 ``Test::Quattor`` defaults to ``linux_sysv``.
 


- ``force_service_variant``
 
 Force the variant by bypassing ``CAF::Service`` ``AUTOLOAD`` magic
 and defining the methods
 via glob assignments in the namespace.
 
 The first argument is the ``$variant`` to use.
 
 When testing subclassed ``CAF::Service``,
 the second (optional) argument is the subclass, followed by
 all other arguments as additional non-standard actions.
 


- set_immutable
 
 Make ``path`` immutable. Pass a false ``bool`` to make the path mutable again
 (not <undef>, default is to make the path immutable).
 


- set_status
 
 (Re)set status of ``path`` to the options (``mode``, ``mtime``, ``owner`` and/or ``group``).
 


- is_mutable
 
 Check if the path and parent path are mutable.
 (Parent path is not checked when ``skip_parent`` argument is true).
 
 Report an error prefixed with ``prefix`` and return 0
 when path (and/or parent path) is immutable.
 


- sane_path
 
 sanitize path by
 
 
 - squash multiple '/' into one
 
 
 
 - remove all trailing '/'
 
 
 


- is_file
 
 Test if given ``$path`` is a mocked file
 


- is_directory
 
 Test if given ``$path`` is a mocked directory
 


- is_any Test if given ``path`` is known (as file or directory or anything else)



- make_directory
 
 Add a directory to the mocked directories.
 If ``rec`` is true or undef, also add all underlying directories.
 
 If ``mutable`` is true, always create the directory.
 
 If directory already exists and is a directory, return SUCCESS (undef otherwise).
 


- remove_any
 
 Recursive removal of a ``path`` from the files_contents / desired_file_contents
 


- move
 
 move ``src`` to ``dest``. If ``backup`` is defined and not empty string,
 move ``dest`` to backup (``backup`` is a suffix).
 


- add_caf_path
 
 Add array of arguments to ``caf_path`` hashref using ``name``
 


- reset_caf_path
 
 Reset ``caf_path`` ref. If ``name`` is defined, only reset that cache.
 


- dump_contents
 
 Debug function to show the entries in ``desired_file_contents``
 and ``files_contents``.
 
 Options
 
 
 - log
  
  Pass a reporter/logger instance, and report with verbose level.
  By default, ``Test::More::diag`` is used.
  
 
 
 - filter
  
  Regex pattern to filter filenames to show (matches are kept).
  
 
 
 - prefix
  
  A message prefix
  
 
 



****
BUGS
****


Probably many. It does quite a lot of internal black magic to make
your executions safe. Please ensure your component doesn't try to
outsmart the ``CAF`` library and everything should be fine.

