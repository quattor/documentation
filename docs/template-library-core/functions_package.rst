###################
functions\::package
###################

Variables
---------

 - PKG_VERSION_GREATER
    - Description: value returned by pkg_compare_version() when the version in the first arugment is greater than the second.
 - PKG_VERSION_EQUAL
    - Description: value returned by pkg_compare_version() when the version in the two version arguments are equal
 - PKG_VERSION_LESS
    - Description: value returned by pkg_compare_version() when the version in the first arugment is lower than the second.

Functions
---------

 - pkg_compare_version
    - Description: function to compare 2 package versions in the form x.y.z-r. It properly handles number comparison of each element (10 is considered greater than 2) and it also accepts letters in one of the element (an alphanumeric value is considered less than a number).
 - pkg_update
