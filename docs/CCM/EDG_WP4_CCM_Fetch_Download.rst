
##################################
EDG\::WP4\::CCM\::Fetch\::Download
##################################


****
NAME
****


EDG::WP4::CCM::Fetch::Download


***********
DESCRIPTION
***********


Module provides methods to handle the retrieval of the profiles.


*********
Functions
*********



- retrieve
 
 Stores $url into $cache if it's newer than $time, or if $self->{FORCE}
 is set.
 
 It returns undef in case of error, 0 if it there were no changes on the
 remote server since ``$time`` (the server returned a 304 code)
 and a ``CAF::FileWriter`` object with the
 downloaded contents if they had to be downloaded.
 
 Should be called ony by ``download``.
 


- download
 
 Downloads the files associated with $type (profile). In
 case of error it retries $self->{RETRIEVE_RETRIES} times, falling back
 to a failover URL if necessary (thus up to 2\*$self->{RETRIEVE_RETRIES}
 may happen.
 
 Returns undef (or dies) in case of error, or the result from ``retrieve`` method otherwise:
 
 
 - 0 if nothing had to be retrieved (files in the server were older than our local cache)
 
 
 
 - a ``CAF::FileWriter`` object with the downloaded contents, if something was actually downloaded
 
 
 


