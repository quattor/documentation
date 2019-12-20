
######################
Quattor\::ProfileCache
######################


***********
DESCRIPTION
***********


Module to setup a profile cache

set_profile_cache_options
=========================


Set additional options for prepare_profile_cache

Set specific values for the ``cache``, ``resources`` and/or ``profiles`` directory.
Will be used by ``get_profile_cache_dirs``


- cache



- resources



- profiles




get_profile_cache_dirs
======================


Return hashreference to the directories used to setup
the profile cache: 'cache', 'resources' and 'profiles'.

The values are generated from the defaults or ``profilecacheoptions``
(to be set via ``set_profile_cache_options``).

Relative paths are assumed to be relative wrt current directory;
absolute paths are used for the returned values.


prepare_profile_cache_panc_includedirs
======================================



prepare_profile_cache
=====================


Prepares a cache for the profile given as an argument. This means
compiling the profile, fetching it and saving the binary cache
wherever the CCM configuration tells us.

Returns the configuration object for this profile.

The ``croak_on_error`` argument is passed to the ``Test::Quattor::Panc::panc`` method.
If this boolean is 0 (and not undef), ``prepare_profile_cache``
will return the ``panc`` exitcode upon ``panc`` failure.


``get_config_for_profile``
==============================


Returns a configuration object for the profile given as an
argument. The profile should be one of the arguments given to
``Test::Quattor`` when loading it.

If the configuration cannot be found, an error is reported, and
a test fails.


``set_json_typed``
======================


Set the json_typed config attribute to ``value``.
If value is undefined, ``json_typed`` is set to true.

Returns the value set.


``get_json_typed``
======================


Return the ``json_typed`` value.


