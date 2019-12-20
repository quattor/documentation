
###############
CAF\::Exception
###############


****
NAME
****


CAF::Exception - provides basic methods for failure and exception handling

Private methods
===============



- _get_noaction
 
 Return NoAction setting:
 
 
 - Return 0 is ``keeps_state`` is true
  
  Any other value of ``keeps_state`` is ignored. (In particular,
  you cannot use ``keeps_state`` to enable NoAction).
  
 
 
 - Return value of ``noAction`` method (when defined)
 
 
 
 - ``CAF::Object::NoAction`` otherwise
 
 
 
 Supports an optional ``msg`` that is prefixed to reporter.
 


- _reset_exception_fail
 
 Reset previous fail attribute and/or exception.
 
 ``msg`` is a suffix when reporting the old ``fail`` attribute
 and/or exception error (with debug level 1).
 
 ``EC`` is a ``LC::Exception::Context`` instance that is checked for an
 existing error, which is set to ignore if it exists.
 
 Always returns SUCCESS.
 


- _function_catch
 
 Execute function reference ``funcref`` with arrayref ``$args`` and hashref ``$opts``.
 
 Method resets any existing fail attribute and error from ``LC::Exception::Context`` instance ``EC``.
 
 When an exception thrown is thrown, it is catched and reset. No error is reported
 and undef is returned in this case and the fail attribute is set with the exception
 error text.
 


- _safe_eval
 
 Run function reference ``funcref`` with arrayref ``argsref`` and hashref ``optsref``.
 
 Return and set fail attribute with ``failmsg`` (``$@`` is added when set) on die
 or in case of an error (``undef`` returned by ``funcref``).
 In case of success, report ``msg`` (stringified result is added unless ``sensitive`` attribute is set)
 at verbose level.
 
 Note that ``_safe_eval`` doesn't work with functions
 that don't return a defined value when they succeed.
 
 Resets previous fail attribute and or exceptions
 (via the ``LC::Exception::Context`` instance ``EC``).
 



