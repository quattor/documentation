
#########################################
EDG\::WP4\::CCM\::CacheManager\::Resource
#########################################


****
NAME
****


EDG::WP4::CCM::CacheManager::Resource - Resource class


********
SYNOPSIS
********



.. code-block:: perl

  %hash = $resource->getHash();
  @list = $resource->getList();
  $boolean = $resource->hasNextElement();
  [$property | $resource] = $resource->getNextElement();
  [$property | $resource] = $resource->getCurrentElement();
  $resource->reset();



***********
DESCRIPTION
***********


The class Resource is a derived class of Element class, and implements
methods that are specific to Resources, that is, internal nodes of
the configuration tree, containing other resources and properties.
tree.


- new($config, $res_path)
 
 Create new Resource object. The $config parameter is a Configuration
 object with the profile. The $res_path parameter is the resource's
 configuration path.
 


- getHash()
 
 Return a hash of elements, indexed by name
 The method raises an exception if the resource type is not nlist
 
 This method is not a part of the NVA-API specification, it may be a
 subject to change.
 


- getList()
 
 Return an array of elements. The method raises an exception
 if the resource type is not list.
 
 This method is not a part of the NVA-API specification, it may be a
 subject to change.
 


- hasNextElement()
 
 Return true if the iteration through Resource has
 more elements, otherwise returns false
 


- getNextElement()
 
 Return the next element in the iteration
 


- getCurrentElement()
 
 Return current element in the iteration. This is the element
 that was returned by the last call of getNextElement()
 


- reset()
 
 Reset the iteration. After this operation being called,
 getNextElement() will return first element in the iteration
 


