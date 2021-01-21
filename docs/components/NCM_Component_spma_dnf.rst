
############################
NCM\::Component\::spma\::dnf
############################


``execute_command``
=======================


Executes ``$command`` for reason ``$why``. Optionally with standard
input ``$stdin``.  The command may be executed even under --noaction if
``$keeps_state`` has a true value.

If the command is executed, this method returns its standard output
upon success or ``undef`` in case of error.  If the command is not
executed the method always returns a true value (usually 1, but don't
rely on this!).

The return value is ordered set of (exit code, stdout, stderr) as a
result of the executed command.

