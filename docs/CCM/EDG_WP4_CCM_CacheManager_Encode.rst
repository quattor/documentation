
#######################################
EDG\::WP4\::CCM\::CacheManager\::Encode
#######################################


****
NAME
****


EDG::WP4::CCM::CacheManager::Encode - Module with DB encoding functions and constants


***********
DESCRIPTION
***********


``EDG::WP4::CCM::CacheManager::Encode`` implements the functions
that provide the encoding of metadata in the DB instance used.

The DB is build as follows:


- In ``EDG::WP4::CCM::Fetch::ProfileCache`` the profile is converted to a hashref with subpath as key and hashref with data and metadata as value.



- The hashref is walked building up the path and a counter (the ``eid``) is increased for each path



- The relation between the path and the counter is stored in the ``path2eid`` DB with path as key and encoded eid (using ``db_keys($eid)->{VALUE}``) as value.



- The data and metadata are stored in ``eid2data`` DB using the encoded eid (which has offset for each type of data and metadata) as key and the data as value.



Access to data based on path is possible without en/decoding (``eid2data->{path2eid->{$path}}``).

Access to the metadata however requires decoding of the encoded eid from path2eid; to recompute
the encoded keys for the metadata.

Type constants:
===============



.. code-block:: perl

   ELEMENT
     PROPERTY
       STRING
       LONG
       DOUBLE
       BOOLEAN
       LINK
     RESOURCE
       NLIST
         TABLE
         RECORD
       LIST



Functions
=========



- type_from_name
 
 Convert a type in string format into a type constant.
 
 Returns ``UNDEFINED`` constant and warns when name is not supported.
 


- decode_eid
 
 Return decoded eid.
 


- encode_eids
 
 Given ``eid``, return the keys of the tie'ed DB hashref
 for ``VALUE``, ``TYPE``, ``DERIVATION``, ``CHECKSUM`` and ``DESCRIPTION``
 as used in the ``eid2data`` DB.
 



