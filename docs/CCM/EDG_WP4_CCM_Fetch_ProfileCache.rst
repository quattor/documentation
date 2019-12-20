
######################################
EDG\::WP4\::CCM\::Fetch\::ProfileCache
######################################


****
NAME
****


EDG::WP4::CCM::Fetch::ProfileCache


***********
DESCRIPTION
***********


Module provides methods to handle the creation of the profile cache.


*********
Functions
*********



- setProfileFormat
 
 Define the profile format. If receives an argument, it will use it
 with no further questions. If not, it will try to derive it from the
 URL, being:
 
 
 * URLs ending in ``xml`` are for XML profiles.
 
 
 
 * URLs ending in ``json`` are for JSON profiles.
 
 
 
 and their gzipped equivalents.
 


