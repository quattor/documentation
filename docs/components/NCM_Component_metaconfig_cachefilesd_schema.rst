###################################################
NCM\::Component\::metaconfig\::cachefilesd - schema
###################################################

Types
-----

 - **/software/components/metaconfig/cachefilesd_service**
    - */software/components/metaconfig/cachefilesd_service/dir*
        - Description: The directory containing the root of the cache.
        - Required
        - Type: string
    - */software/components/metaconfig/cachefilesd_service/secctx*
        - Description: security context as which the kernel will perform operations to access the cache
        - Optional
        - Type: string
    - */software/components/metaconfig/cachefilesd_service/bcull*
        - Description: culling limits, in percent
        - Optional
        - Type: long
        - Range: 0..100
    - */software/components/metaconfig/cachefilesd_service/brun*
        - Optional
        - Type: long
        - Range: 0..100
    - */software/components/metaconfig/cachefilesd_service/bstop*
        - Optional
        - Type: long
        - Range: 0..100
    - */software/components/metaconfig/cachefilesd_service/fcull*
        - Optional
        - Type: long
        - Range: 0..100
    - */software/components/metaconfig/cachefilesd_service/frun*
        - Optional
        - Type: long
        - Range: 0..100
    - */software/components/metaconfig/cachefilesd_service/fstop*
        - Optional
        - Type: long
        - Range: 0..100
    - */software/components/metaconfig/cachefilesd_service/tag*
        - Description: a tag to distinguish multiple caches
        - Optional
        - Type: string
    - */software/components/metaconfig/cachefilesd_service/culltable*
        - Description: The size of the tables holding the lists of cullable objects in the cache in log2
        - Optional
        - Type: long
        - Range: 12..20
    - */software/components/metaconfig/cachefilesd_service/nocull*
        - Description: Disable culling
        - Optional
        - Type: boolean
    - */software/components/metaconfig/cachefilesd_service/debug*
        - Description: a numeric bitmask to control debugging in the kernel module
        - Optional
        - Type: long
        - Range: 0..7
