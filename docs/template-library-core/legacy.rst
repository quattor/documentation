######
legacy
######

Types
-----

 - **legacy_binary_affirmation_string**
    - Description: Common type to replace all variants of yes/no pseudo boolean strings throughout components
 - **transitional_yes_no_true_false**
    - Description: Transitional type to allow components to cleanly migrate properties from yes/no strings to booleans No components shall use this type until it has been made compatible with real booleans No component shall use this type for more than a single release
 - **transitional_string_or_list_of_strings**
    - Description: Transitional type to allow components to cleanly migrate properties from a string to a list of strings No components shall use this type until they have been made compatible with list of strings

Functions
---------

 - is_yes_no_true_false
    - Description: Validate a property to either be a boolean or a yes/no string Used to implement transitional_yes_no_true_false
 - is_string_or_list_of_strings
    - Description: Validate that a property is either a string, or a list of strings An empty string or list is permitted Used to implement transitional_string_or_list_of_strings
