
##########
CAF\::Lock
##########


****
NAME
****


CAF::Lock - Class for handling application instance locking


********
SYNOPSIS
********



.. code-block:: perl

     use CAF::Lock;
 
     $lock = CAF::Lock->new('/var/lock/quattor/spma', log => $reporter);
 
     unless ($lock->set_lock()) {...}
     unless ($lock->set_lock(10, 2) {...}
     unless ($lock->set_lock(3, 3, FORCE_ALWAYS)) {...}
 
     unless ($lock->unlock()) {....}



***********
INHERITANCE
***********



.. code-block:: perl

     CAF::Object



***********
DESCRIPTION
***********


The \ **CAF::Lock**\  class provides methods for handling application locking.


**************
PUBLIC METHODS
**************



- set_lock(\ *retries*\ , \ *timeout*\ , \ *force*\ )
 
 Tries \ *retries*\  times to set the lock.  If \ *force*\  is set to \ **FORCE_NONE**\ 
 or not defined and the lock is set, it sleeps for \ *timeout*\ .  Returns
 \ **SUCCESS**\ , or \ **undef**\  on failure.
 
 If \ *retries*\  or \ *timeout*\  are not defined or set to 0, only a single
 attempt is done to acquire the lock.
 
 If \ *force*\  is set to \ **FORCE_ALWAYS**\  then the lock file is just set
 again, even if the lock is already set by another application
 instance, and neither \ *timeout*\  nor \ *retries*\  are taken
 into account.
 


- unlock()
 
 Releases the lock and returns \ **SUCCESS**\ .  Reports an error and returns
 \ **undef**\  if the lock cannot be released.  If the object (application
 instance) does not hold the lock, an error is reported and \ **undef**\ 
 is returned.
 


- is_set()
 
 Returns \ **SUCCESS**\  if lock is set by application instance, \ **undef**\  otherwise.
 



***************
PRIVATE METHODS
***************



- _initialize(\ *lockfilename*\ )
 
 Initialize the object.  Called by new(\ *lockfilename*\ ).
 
 Optional arguments
 
 
 - ``log``
  
  A ``CAF::Reporter`` object to log to.
  
 
 


- _try_lock(\ *force*\ )
 
 Called by set_lock() to create the lock file and return \ **SUCCESS**\  if we were
 able to flock() the file.
 
 If \ *force*\  is set to \ **FORCE_ALWAYS**\  then this method will return \ **SUCCESS**\ 
 even if flock() was unsuccessful.
 


