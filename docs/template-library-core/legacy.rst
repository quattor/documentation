######
legacy
######

Types
-----

 - **legacy_binary_affirmation_string**
    - Description: Common type to replace all variants of yes/no pseudo boolean strings throughout components
 - **transitional_yes_no_true_false**
    - Description: Transitional type to allow components to cleanly migrate properties from yes/no strings to booleans No components shall use this type until it has been made compatible with real booleans No component shall use this type for more than a single release

Functions
---------

 - is_yes_no_true_false
    - Description: Validate a property to either be a boolean or a yes/no string Used to implement transitional_yes_no_true_false
