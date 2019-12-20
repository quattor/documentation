
######################
EDG\::WP4\::CCM\::Path
######################


****
NAME
****


EDG::WP4::CCM::Path - Path class


********
SYNOPSIS
********



.. code-block:: perl

     $path = EDG::WP4::CCM::Path->new("/hardware/memory/size");
     print "$path"; # stringification
 
     $path = $path->down($level);
 
     $path = $path->up();



***********
DESCRIPTION
***********


Module provides implementation of the Path class. Class is used
to manipulate absolute paths

Public methods
==============



- new ($path)
 
 Create new ``EDG::WP4::CCM::Path`` instance.
 
 If ``path`` argument is not specified, root path (``/``) is used.
 Empty string is not allowed as an argument.
 
 ``path`` is a string representation of the path as defined in the NVA-API
 Specification document.
 


- depth
 
 Return the number of subpaths, starting from ``/``.
 


- get_last
 
 Return last (safe unescaped) subpath or undef in case of ``/``.
 The ``strip_unescape`` boolean is passed to ``_safe_unescape``.
 


- toString
 
 Get the (raw) string representation of path.
 
 The ``EDG::WP4::CCM::Path`` instances also support stringification
 (the ``_stringify`` method is used for that) and might create different result
 due to ``safe_unescape``.
 


- _boolean
 
 bool overload: ``Path`` instance is always true (avoids stringification on logic test)
 


- _stringify
 
 Method for overloaded stringification.
 
 This includes support for ``safe_unescape`` to wrap
 unescaped subpaths in ``{}``.
 


- up
 
 Removes last chunk of the path and returns it.
 If the path is already ``/`` then the method
 raises an exception.
 


- down
 
 Add ``chunk`` to the path. The chunk can be compound path.
 (A leading ``/`` will be ignored).
 


- merge
 
 Return a new instance with optional (list of) subpaths added.
 


- parent
 
 Return a new instance with parent path.
 Returns undef if current element is ``/``.
 



Public functions
================



- unescape
 
 Returns an unescaped version of the argument. This method is exported
 for use with all the components that deal with escaped keys.
 


- escape
 
 Returns an escaped version of the argument.  This method is exported on
 demand for use with all tools that have to escape and unescape values.
 


- path_split
 
 Function to split a string in list of subpaths.
 Supports escaping of subpaths wrapped in ``{...}``.
 


- set_safe_unescape
 
 Set the list of (parent) paths whose children are known to be escaped paths.
 (The list is set to all arguments passed, not appended to current safe_unescape list).
 
 Paths can either be strings (an exact match will be used)
 or compiled regular expressions.
 
 These child subpaths are safe to represent as their unescaped value
 wrapped in ``{}`` when <toString> method is called (e.g. during stringification).
 
 Parent paths who have a safe-to escape parent path of their own should be added
 already escaped.
 
 The list is stored in the ``safe_unescape`` module variable and
 can emptied with ``reset_safe_unescape`` exported functions.
 
 If no argument is passed, a predefined list of paths is used. The paths are known
 to be escaped in quattor profiles, e.g. ``/software/components/metaconfig/services``.
 (To reset the active ``safe_unescape`` list, use ``reset_safe_unescape`` function.
 


- reset_safe_unescape
 
 Reset the ``safe_unescape`` list.
 


- _safe_unescape
 
 Given ``path`` and ``subpath``, test is ``path`` is in ``@safe_unescape``
 and if it is, return unescaped subpath enclosed in ``{}`` (or not enclosed if
 ``strip_unescape`` is true).
 
 If not, return unmodified subpath.
 



