
#######################
EDG\::WP4\::CCM\::Fetch
#######################


****
NAME
****


EDG::WP4::CCM::Fetch


********
SYNOPSIS
********



.. code-block:: perl

   $fetch = EDG::WP4::CCM::Fetch->new({PROFILE_URL => "profile_url or hostname",
                       CONFIG  => "path of config file",
                       FOREIGN => "1/0"});
 
 
   $fetch->fetchProfile();



***********
DESCRIPTION
***********


Module provides Fetch class. This helps in retrieving XML profiles and
from specified URLs. It allows users to retrieve local, as
well as foreign node profiles.


*********
Functions
*********



- new()
 
 
 .. code-block:: perl
 
    new({PROFILE_URL => "profile_url or hostname",
         CONFIG  => "path of config file",
         FOREIGN => "1/0"});
 
 
 Creates new Fetch object. Full url of the profile can be provided as
 parameter PROFILE_URL, if it is not a url a profile url will be
 calculated using 'base_url' config option in `/etc/ccm.conf`.  Path of
 alternative configuration file can be given as CONFIG.
 
 Returns undef in case of error.
 


- fetchProfile()
 
 fetchProfile  fetches the  profile  from  profile url and keeps it at
 configured area.  The  cache  root variable is set as
 $fetch_handle{'CACHE_ROOT'} which can further be passed to CacheManager
 object and use NVA-API to access Resources and Properties.
 
 If the profile is foreign, then the cache_root configuration is expected
 to be just for this foreign host and unexpected behaviour will result
 if the cache_root is shared. Only a single (most recent) copy of the
 foreign copy will be stored: previous versions will be removed. Foreign
 profiles do not use failover URLs: if the primary URL is unavailable,
 then the fetch will fail.
 
 Returns undef if it cannot fetch the profile due to a network error,
 ``<$EDG::WP4::CCM::Fetch::ProfileCache::ERROR``> in case of other failure,
 ``SUCCESS`` in case of successful fetch, but no updated profile
 and ``CHANGED`` in case of successful fetch and
 updated profile.
 


