
#############
CAF\::Process
#############


****
NAME
****


CAF::Process - Class for running commands in CAF applications


********
SYNOPSIS
********



.. code-block:: perl

     use CAF::Process;
     my $proc = CAF::Process->new ([qw (my command)], log => $self);
     $proc->pushargs (qw (more arguments));
     my $output = $proc->output();
     $proc->execute();



***********
DESCRIPTION
***********


This class provides a convenient wrapper to LC::Process
functions. Commands are logged at the verbose level.

All these methods return the return value of their LC::Process
equivalent. This is different from the command's exit status, which is
stored in ``$?``.

Please use these functions, and \ **do not**\  use ``\`\```, ``qx//`` or
``system``. These functions won't spawn a subshell, and thus are more
secure.

Private methods
===============



- ``_initialize``
 
 Initialize the process object. Arguments:
 
 
 - ``$command``
  
  A reference to an array with the command and its arguments.
  
 
 
 - ``%opts``
  
  A hash with the command options:
  
  
  - ``log``
   
   The log object. If not supplied, no logging will be performed.
   
  
  
  - ``timeout``
   
   Maximum execution time, in seconds, for the command. If it's too slow
   it will be killed.
   
  
  
  - ``pid``
   
   Reference to a scalar that will hold the child's PID.
   
  
  
  - ``stdin``
   
   Data to be passed to the child's stdin
   
  
  
  - ``stdout``
   
   Reference to a scalar that will have child's stdout
   
  
  
  - ``stderr``
   
   Reference to a scalar that will hold the child's stderr.
   
  
  
  - ``keeps_state``
   
   A boolean specifying whether the command respects the current system
   state or not. A command that ``keeps_state`` will be executed,
   regardless of any value for ``NoAction``.
   
   By default, commands modify the state and thus ``keeps_state`` is
   false.
   
  
  
  - ``sensitive``
   
   A boolean, hashref or functionref specifying whether the arguments contain
   sensitive information (like passwords).
   
   If ``sensitive`` is true, the commandline will not be reported
   (by default when ``log`` option is used, the commandline is reported
   with verbose level).
   
   If ``sensitive`` is a hash reference, a basic search (key) and replace (value) is performed.
   The keys and values are not interpreted as regexp patterns. The order of the search and
   replace is determined by the sorted values (this gives you some control over the order).
   Be aware that all occurences are replaced, and when e.g. weak passwords are used,
   it might reveal the password by replacing other parts of the commandline
   (``--password=password`` might be replaced by ``--SECRET=SECRET``,
   thus revealing the weak password).
   Also, when a key is a substring of another key,
   it will reveal (parts of) sensitive data if the order is not correct.
   
   If ``sensitive`` is a function reference, the command arrayref is passed
   as only argument, and the stringified return value is reported.
   
   
   .. code-block:: perl
   
        my $replace = sub {
            my $command = shift;
            return join("_", @$command);
        };
    
        ...
    
        CAF::Process->new(..., sensitive => $replace);
   
   
   This does not cover command output. If the output (stdout and/or stderr) contains
   sensitve information, make sure to handle it yourself via ``stdout`` and/or ``stderr``
   options (or by using the ``output`` method).
   
  
  
  These options will only be used by the execute method.
  
 
 


- _sensitive_commandline
 
 Generate the reported command line text, in particular it deals with
 the ``sensitive`` attribute.
 When the sensitive attribute is not set, it returns ``stringify_command``.
 
 This method does not report, only returns text.
 
 See the description of the ``sensitive`` option in ``_initialize``.
 


- _LC_Process
 
 Run ``LC::Process`` ``function`` with arrayref arguments ``args``.
 
 ``noaction_value`` is is the value to return with ``NoAction``.
 
 ``msg`` and ``postmsg`` are used to construct log message
 ``<msg> command: <COMMAND>[ <postmsg>]``.
 



Public methods
==============



- execute
 
 Runs the command, with the options passed at initialization time. If
 running on verbose mode, the exact command line and options are
 logged.
 
 Please, initialize the object with ``log => ''`` if you are passing
 confidential data as an argument to your command.
 



- output
 
 Returns the output of the command. The output will not be logged for
 security reasons.
 



- toutput
 
 Returns the output of the command, that will be run with the timeout
 passed as an argument. The output will not be logged for security
 reasons.
 



- stream_output
 
 Execute the commands using ``execute``, but the ``stderr`` is
 redirected to ``stdout``, and ``stdout`` is processed with ``process``
 function. The total output is aggregated and returned when finished.
 
 Extra option is the process ``mode``. By default (or value ``undef``),
 the new output is passed to ``process``. With mode ``line``, ``process``
 is called for each line of output (i.e. separated by newline), and
 the remainder of the output when the process is finished.
 
 Another option are the process ``arguments``. This is a reference to the
 array of arguments passed to the ``process`` function.
 The arguments are passed before the output to the ``process``: e.g.
 if ``arguments =\> [qw(a b)]`` is used, the ``process`` function is
 called like ``process(a,b,$newoutput)`` (with ``$newoutput`` the
 new streamed output)
 
 Example usage: during a ``yum install``, you want to stop the yum process
 when an error message is detected.
 
 
 .. code-block:: perl
 
      sub act {
          my ($self, $proc, $message) = @_;
          if ($message =~ m/error/) {
              $self->error("Error encountered, stopping process: $message");
              $proc->stop;
          }
      }
  
      $self->info("Going to start yum");
      my $p = CAF::Process->new([qw(yum install error)], input => 'init');
      $p->stream_output(\&act, mode => line, arguments => [$self, $p]);
 
 



- run
 
 Runs the command.
 



- trun
 
 Runs the command with $timeout seconds of timeout.
 



- pushargs
 
 Appends the arguments to the list of command arguments
 



- setopts
 
 Sets the hash of options passed to the options for the command
 



- stringify_command
 
 Return the command and its arguments as a space separated string.
 



- get_command
 
 Return the reference to the array with the command and its arguments.
 



- get_executable
 
 Return the executable (i.e. the first element of the command).
 



- is_executable
 
 Checks if the first element of the
 array with the command and its arguments, is executable.
 
 It returns the result of the ``-x`` test on the filename
 (or ``undef`` if filename can't be resolved).
 
 If the filename is equal to the ``basename``, then the
 filename to test is resolved using the
 ``File::Which::which`` method.
 (Use ``./script`` if you want to check a script in the
 current working directory).
 



- execute_if_exists
 
 Execute after verifying the executable (i.e. the first
 element of the command) exists and is executable.
 
 If this is not the case the method returns 1.
 




****************
COMMON USE CASES
****************


On the next examples, no log is used. If you want your component to
log the command, just add ``log => $self`` to the object creation.

Running a command
=================


First, create the command:


.. code-block:: perl

     my $proc = CAF::Process->new (["ls", "-lh"]);


Then, choose amongst:


.. code-block:: perl

     $proc->run();
     $proc->execute();



Emulating backticks to get a command's output
=============================================


Create the command:


.. code-block:: perl

     my $proc = CAF::Process->new (["ls", "-lh"]);


And get the output:


.. code-block:: perl

     my $output = $proc->output();



Piping into a command's stdin
=============================


Create the contents to be piped:


.. code-block:: perl

     my $contents = "Hello, world";


Create the command, specifying ``$contents`` as the input, and
``execute`` it:


.. code-block:: perl

     my $proc = CAF::Process->new (["cat", "-"], stdin => $contents);
     $proc->execute();



Piping in and out
=================


Suppose we want a bi-directional pipe: we provide the command's stdin,
and need to get its output and error:


.. code-block:: perl

     my ($stdin, $stdout, $stderr) = ("Hello, world", undef, undef);
     my $proc = CAF::Process->new (["cat", "-"], stdin => $stdin,
                                   stdout => \$stdout
                                   stderr => \$stderr);
     $proc->execute();


And we'll have the command's standard output and error on $stdout and
$stderr.


Creating the command dynamically
================================


Suppose you want to add options to your command, dynamically:


.. code-block:: perl

     my $proc = CAF::Process->new (["ls", "-l"]);
     $proc->pushargs ("-a", "-h");
     if ($my_expression) {
         $proc->pushargs ("-S");
     }
 
     # Runs ls -l -a -h -S
     $proc->run();



Subshells
=========


Okay, you \ **really**\  want them. You can't live without them. You found
some obscure case that really needs a shell. Here is how to get
it. But please, don't use it without a \ **good**\  reason:


.. code-block:: perl

     my $cmd = CAF::Process->new(["ls -lh|wc -l"], log => $self,
                                  shell => 1);
     $cmd->execute();


It will only work with the ``execute`` method.


