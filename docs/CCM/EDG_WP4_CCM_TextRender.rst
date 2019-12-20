
############################
EDG\::WP4\::CCM\::TextRender
############################


****
NAME
****


CCM::TextRender - Class for rendering structured text using Element instances


***********
DESCRIPTION
***********


This class is an extension of the ``CAF::TextRender`` class; with the main
difference the support of a ``EDG::WP4::CCM::CacheManager::Element`` instance as contents.

Private methods
===============



- ``_initialize``
 
 Initialize the process object. Arguments:
 
 
 - module
  
  The rendering module to use (see \ **CAF::TextRender**\  for details).
  
  CCM provides following additional builtin modules:
  
  
  - general
   
   using TT to render a ``Config::General`` compatible file.
   (This is an alias for the ``CCM/general`` TT module).
   
   Contents is a hashref (does not require a ``Element`` instance),
   with key/value pairs generated according to
   the basetype of the value as follows:
   
   
   - scalar
    
    converted in a single line
    
    
    .. code-block:: perl
    
         <key> <value>
    
    
   
   
   - arrayref of scalars
    
    converted in multiple lines as follows
    
    
    .. code-block:: perl
    
         <key> <scalar element0>
         <key> <scalar element1>
         ...
    
    
   
   
   - hashref
    
    generates a block with format
    
    
    .. code-block:: perl
    
         <"key">
             <recursive rendering of the value>
         </"key">
    
    
   
   
   - arrayref of hashref
    
    generates series of blocks
    
    
    .. code-block:: perl
    
         <"key">
             <recursive rendering of the element0>
         </"key">
         <"key">
             <recursive rendering of the element1>
         </"key">
         ...
    
    
   
   
   (Whitespace in the block name is enforced with double quotes.)
   
  
  
 
 
 - contents
  
  ``contents`` is either a hash reference holding the contents to pass to the rendering module;
  or a ``EDG::WP4::CCM::CacheManager::Element`` instance, on which ``getTree`` is called with any ``element``
  options.
  
 
 
 All optional arguments from ``CAF::TextRender`` are supported unmodified:
 
 
 - log
 
 
 
 - includepath
 
 
 
 - relpath
 
 
 
 - eol
 
 
 
 - usecache
 
 
 
 - ttoptions
 
 
 
 Extra optional arguments:
 
 
 - element
  
  A hashref holding any ``getTree`` options to pass. These can be the
  anonymous convert methods ``convert_boolean``, ``convert_string``,
  ``convert_long`` and ``convert_double``; or one of the
  predefined convert methods (key is the name, value a boolean
  wheter or not to use them).
  
  The ``convert_`` methods are added as last methods.
  
  The predefined convert methods are:
  
  
  - cast
   
   Convert the scalar values to a more exact internal representation.
   The internal representaiton is important when passed on to other
   non-pure perl code, in particular the ``XS`` modules like ``JSON::XS``
   and ``YAML::XS``.
   
  
  
  - json
   
   Enable JSON output, in particular JSON boolean (``cast`` is implied,
   so the other types should already be in proper format).
   This is automatically enabled when the json
   module is used (and not explicitly set).
   
  
  
  - yaml
   
   Enable YAML output, in particular YAML boolean (``cast`` is implied,
   so the other types should already be in proper format).
   This is automatically enabled when the yaml
   module is used (and not explicitly set).
   
  
  
  - yesno
   
   Convert boolean to (lowercase) 'yes' and 'no'.
   
  
  
  - YESNO
   
   Convert boolean to (uppercase) 'YES' and 'NO'.
   
  
  
  - truefalse
   
   Convert boolean to (lowercase) 'true' and 'false'.
   
  
  
  - TRUEFALSE
   
   Convert boolean to (uppercase) 'TRUE' and 'FALSE'.
   
  
  
  - doublequote
   
   Convert string to doublequoted string.
   
  
  
  - singlequote
   
   Convert string to singlequoted string.
   
  
  
  - joincomma
   
   Convert list of scalars in comma-separated list of strings
   (if first element is scalar). List where first element is
   non-scalar is not converted (but any of the nested list could).
   
  
  
  - joinspace
   
   Convert list of scalars in space-separated list of strings
   (if first element is scalar). List where first element is
   non-scalar is not converted (but any of the nested list could).
   
   Caveat: is preceded by ``joincomma`` option.
   
  
  
  - unescapekey
   
   Unescape all dict keys.
   
  
  
  - lowerkey
   
   Convert all dict keys to lowercase.
   
  
  
  - upperkey
   
   Convert all dict keys to uppercase.
   
  
  
  Other ``getTree`` options
  
  
  - depth
   
   Only return the next ``depth`` levels of nesting (and use the
   Element instances as values). A ``depth == 0`` is the element itself,
   ``depth == 1`` is the first level, ...
   
   Default or depth ``undef`` returns all levels.
   
  
  
 
 


- ccm_format
 
 Returns the CCM::TextRender instance for predefined ``format`` and ``element``.
 All options are passed to CCM::TextRender initialisation.
 Returns undef incase the format is not defined. An array with valid formats is
 exported via ``@CCM_FORMATS``.
 
 Supported formats are:
 
 
 - json
 
 
 
 - jsonpretty
 
 
 
 - pan
 
 
 
 - pancxml
 
 
 
 - query
 
 
 
 - yaml
 
 
 
 Usage example:
 
 
 .. code-block:: perl
 
      use EDG::WP4::CCM::TextRender qw(ccm_format);
      my $format = 'json';
      my $element = $config->getElement("/");
      my $trd = ccm_format($format, $element);
  
      if (defined $trd->get_text()) {
          print "$trd";
      } else {
          $logger->error("Failed to textrender format $format: $trd->{fail}")
      }
 
 



