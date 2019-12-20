
##########################################
EDG\::WP4\::CCM\::Fetch\::JSONProfileTyped
##########################################


********
SYNOPSIS
********



.. code-block:: perl

     EDG::WP4::CCM::Fetch::JSONProfileTyped->interpret_node($tag, $jsondoc);



***********
DESCRIPTION
***********


Module that iterprets a JSON profile and generates all the needed
metadata, to be inserted in the cache DB.

This metadata includes a checksum for each element in the profile, the
Pan basic type, the element's name (that will help to reconstruct the path)...

Should be used by ``EDG::WP4::CCM::Fetch`` only.

This module has only ``interpret_node`` method for the outside world.

Type information from JSON::XS
==============================


JSON profiles don't contain any explicit type information (as opposed to the
XMLPAN output), e.g. JSON only supports 'number' where XMLPAN has 'long' and 'double'.

It is up to the JSON decoder to provide us with this additional distinction.
The JSON package ``JSON::XS`` does not expose the scalar type information.

However, we try to come up with correct proper type by relying on the property that
``JSON::XS`` supports ``json_string eq encode(copy(decode(json_string)))``
(implying that the instance returned by ``decode`` has the ``XS`` types
(and e.g. no stringification has happened)). However, this is best effort only.

Imperative in the whole typed processing is that values from the decoded JSON
are not assigned to any variable before the type information is extraced via the
``B::svref_2object`` method. The scalar types (except for boolean) are then mapped to
the ``B`` classes: ``IV`` is 'long', ``PV`` is 'double' and ``NV`` is 'string'.
Anything else will be mapped to string (including the combined classes ``PVNV`` and ``PVIV``).

TODO: The validity of this assumption is tested in the ``BEGIN{}`` (and unittests).


``interpret_node``
======================


``b_obj`` is returned by the ``B::svref_2object()`` method on the ``doc``
(ideally before ``doc`` is assigned).

The initial call from ``Fetch`` doesn't pass the ``b_obj`` value, but that is
acceptable since we do not expect the whole JSON profile to be a single scalar value.


