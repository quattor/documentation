
### SYNOPSIS

    EDG::WP4::CCM::Fetch::XMLPanProfile->interpret_node($tag, $xmltree);

### DESCRIPTION

Module that iterprets an XML profile in `pan` format, and generates
all the needed metadata, to be inserted in the cache DB.

This metadata includes a checksum for each element in the profile, the
Pan basic type, the element's name (that will help to reconstruct the path)...

Should be used by `EDG::WP4::CCM::Fetch` only.

This module has only one method for the outside world:

#### `interpret_node`

Interprets an XML tree, which is assumed to have a `format="pan"`
attribute, returning the appropriate data structure with all the
attributes and values.
