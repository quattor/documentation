
########################
NCD\::ComponentProxyList
########################


****
NAME
****


NCD::ComponentProxyList - component proxy list class


***********
INHERITANCE
***********



.. code-block:: perl

   CAF::Object, CAF::Reporter



***********
DESCRIPTION
***********


Instantiation, execution and management of ComponentProxy object instances.

Public methods
==============




Private methods
===============



- _initialize($config, $skip, \@comp_names)
 
 object initialization (done via new)
 


- _set_state
 
 Convenience method to wrap around ``set_state`` function,
 passing ``noaction`` and ``statedir`` from current options
 and using ``self`` as logger.
 



Functions
=========



- get_statefile
 
 Return the statefile filename for component ``comp`` in the
 ``statedir``. Statedir is created if it doesn't exist previously
 Return undef in case of problem.
 
 First argument is a ``CAF::Reporter`` instance for logging.
 


- set_state
 
 Mark a component ``comp`` as failed within our state directory
 by wrtiting message ``msg`` to the statefile in ``statedir``.
 
 Returns undef with ``noaction`` argument (from noaction option),
 1 otherwise.
 
 First argument is a ``CAF::Reporter`` instance for logging.
 



