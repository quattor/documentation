
### NAME

    CCM::TextRender::Scalar - Class to access scalar/property Element attributes within TT.

### DESCRIPTION

This is a wrapper class to access some scalar/property Element attributes
(in particular the type) within TT.

#### Methods

- new

    Create a new instance with `value` and `type`.

- \_stringify

    Method called to stringification. Simply returns the data in string context

- get\_type

    Return TYPE attribute

- get\_value

    Return value (i.e. the VALUE attribute)
    (can be useful in case the overloading behaves unexpected)

- is\_boolean

    Return true if the TYPE is boolean

- is\_string

    Return true if the TYPE is string

- is\_double

    Return true if the TYPE is double

- is\_long

    Return true if the TYPE is long
