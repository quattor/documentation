
### SYNOPSIS

    EDG::WP4::CCM::Fetch::JSONProfileSimple->interpret_node($tag, $jsondoc);

### DESCRIPTION

Module that iterprets a JSON profile and generates all the needed
metadata, to be inserted in the cache DB.

This metadata includes a checksum for each element in the profile, the
Pan basic type, the element's name (that will help to reconstruct the path)...
JSONProfileSimple only support 2 scalars: booleans and strings.

Should be used by `EDG::WP4::CCM::Fetch` only.

This module has only one method for the outside world:

#### `interpret_node`

JSON profiles don't contain any basic type information, and JSON::XS
may lose it. So, with JSONProfileSimple, we'll store in the caches only two types
of scalars: booleans, which will be identical as they used to be, and
strings.

Component writers know if they expect a given element in the profile
to be a number, and may rely on Perl's automatic
stringification/numification.
