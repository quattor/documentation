
########################################
EDG\::WP4\::CCM\::CacheManager\::Element
########################################


****
NAME
****


EDG::WP4::CCM::CacheManager::Element - Element class


********
SYNOPSIS
********



.. code-block:: perl

     $eid = $element->getEID();
     $name = $element->getName();
     $path = $element->getPath()
     $type = $element->getType();
     $derivation = $element->getDerivation();
     $checksum = $element->getChecksum();
     $description = $element->getDescription();
     $value = $element->getValue();
     $boolean = $element->isType($type);
     $boolean = $element->isResource();
     $boolean = $element->isProperty();
     $hashref = $element->getRecHash();



***********
DESCRIPTION
***********


The class ``EDG::WP4::CCM::CacheManager::Element`` implements those methods
that are common to all elements and represents a ``Property``.
The class <EDG::WP4::CCM::CacheManager::Element> is a base class for
``EDG::WP4::CCM::CacheManager::Resource``, which has additional methods.


- new($config, $ele_path)
 
 Create new Element object. The $config parameter is a Configuration
 object with the profile. The $ele_path parameter is the element's
 configuration path (it can be either a Path object or a string).
 


- _get_tied_db
 
 Wrapper around read_db() to attempt to cache the tied
 hash.  Takes a scalar reference (to be filled in with either a new
 hash ref or the cached hash ref) instead of a hash ref.
 
 The caching mechanism is extremely conservative and will only cache
 the last version of path2eid or eid2path to be accessed.  It makes
 the assumption that these files will never change.  (Instead, new
 profile data goes into a whole new path.)
 


- elementExists($config, $ele_path)
 
 Returns true if the element identified by $ele_path exists
 otherwise false is returned
 


- createElement($config, $ele_path)
 
 Create a new Resource or Element object, depending on the type of
 the element given by $ele_path. The $config parameter is a Configuration
 object with the profile. The $ele_path parameter is the element's
 configuration path (it can be either a Path object or a string).
 


- getConfiguration()
 
 Returns the element's Configuration object
 


- getEID()
 
 Returns the Element ID of the object.
 
 This method is not a part of the NVA-API specification, it may be a subject
 to change.
 


- getName()
 
 Returns the name of the object
 


- getPath()
 
 Returns a Path object with the element's path
 


- getType()
 
 Returns the element's type, that is, one of the ``TYPE_\*`` constans
 


- getDerivation()
 
 Returns the element's derivation
 


- getChecksum()
 
 Returns the element's checksum (that is, MD5 digest)
 


- getDescription()
 
 Returns the element's description
 


- getValue()
 
 Returns the element's value, as a string
 
 This method is not a part of the NVA-API specification, it may be a subject
 to change.
 


- isType($type)
 
 Returns true if the element's type match type contained in argument $type
 


- isResource()
 
 Return true if the element's type is RESOURCE
 


- isProperty()
 
 Return true if the element's type is PROPERTY
 


- getTree
 
 Returns a reference to a nested hash composed of all elements below
 this element.  Corrected according to the III Quattor Workshop
 recomendations. Now, PAN booleans map to Perl booleans, PAN lists map
 to Perl array references and PAN nlists map to Perl hash references.
 
 Note that links cannot be followed.
 
 If ``depth`` is specified (and not ``undef``), only return the next ``depth``
 levels of nesting (and use the Element instances as values).
 A ``depth == 0`` is the element itself, ``depth == 1`` is the first level, ...
 
 Named options
 
 
 - convert_boolean
  
  Array ref of anonymous methods to convert the argument
  (1 or 0 for resp true and false) to another boolean representation.
  
 
 
 - convert_string
  
  Array ref of anonymous methods to convert the argument
  (string value) to another representation/format.
  
 
 
 - convert_long
  
  Array ref of anonymous methods to convert the argument
  (integer/long value) to another representation/format.
  
 
 
 - convert_double
  
  Array ref of anonymous methods to convert the argument
  (float/double value) to another representation/format.
  
 
 
 - convert_list
  
  Array ref of anonymous methods to convert the argument
  (list of elements) to another representation/format.
  
  Each element is already processed before the conversion.
  
 
 
 - convert_nlist
  
  Array ref of anonymous methods to convert the argument
  (dict of elements) to another representation/format.
  
  Each element is already processed before the conversion.
  
 
 
 - convert_key
  
  Array ref of anonymous methods to convert the key(s) of the dicts
  to another representation/format.
  
  At the end, a stringification of the result is used as key.
  
 
 
 The arrayref of anonymous methods are applied as follows:
 convert methods ``[a, b, c]`` will produce ``$new = c(b(a($old)))``.
 (An exception is thrown if these methods are not code references).
 


