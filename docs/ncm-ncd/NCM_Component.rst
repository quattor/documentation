
###############
NCM\::Component
###############


****
NAME
****


NCM::Component - basic support functions for NCM components


***********
INHERITANCE
***********



.. code-block:: perl

   CAF::Object



***********
DESCRIPTION
***********


This class provides the neccessary support functions for components,
which have to inherit from it.


**************
Public methods
**************



- warn
 
 Report with loglevel 'WARN'. Increases the number of
 reported warnings in the ``WARNINGS`` attribute by 1.
 
 (The ncd client will report the number of warnings reported by the component.)
 


- error
 
 Report with loglevel 'ERROR'. Increases the number of
 reported errors in the ``ERRORS`` attribute by 1.
 
 (The ncd client will report the number of errors reported by the component.
 The component will therefore be flagged as
 failed, and no depending components will be executed.)
 


- name
 
 Returns the component name
 


- prefix
 
 Returns the standard configuration path for the component
 ``</software/components/<name``>>.
 


- get_warnings(): integer
 
 Returns the number of calls to 'warn' by the component.
 


- get_errors(): integer
 
 Returns the number of calls to 'error' by the component.
 


- event
 
 Add an event to the history (if exists). Following metadata is added
 
 
 - component
  
  The component name
  
 
 
 - component_module
  
  The component module
  
 
 
 All other arguments are passed on unmodified.
 


- event_report
 
 Report any relevant events:
 
 
 - events triggered by this component
 
 
 
 - modified files
 
 
 
 Returns arrayref with reported event indices.
 


- set_active_config
 
 Set ``config`` as the ``ACTIVE_CONFIG`` attribute.
 
 Returns the current active config.
 


- get_tree
 
 Return ``EDG::WP4::CCM::Configuration-``getTree> on the ``ACTIVE_CONFIG`` attribute.
 
 All arguments are passed to ``getTree``.
 
 If no arguments are specified, the path passed to ``getTree`` is
 the component prefix (using the ``prefix`` method).
 
 If the path specified is not absolute, the path passed to ``getTree`` is
 prefixed with the component prefix (using the ``prefix`` method).
 
 Returns undef on failure, with ``fail`` attribute set in case of an error.
 
 (Requires active configuration set).
 


- get_fqdn
 
 Return the fqdn based on the current active config.
 
 This is either ``/system/network/realhostname`` (if defined)
 or ``</system/network/hostname>.</system/network/domainname>``.
 
 (Requires active configuration set).
 



********************
Pure virtual methods
********************



- Configure($config): boolean
 
 Component Configure method. Has to be overwritten if used.
 


- Unconfigure($config): boolean
 
 Component Unconfigure method. Has to be overwritten if used.
 



***************
Private methods
***************



- _initialize
 
 object initialization (done via new)
 
 Arguments
 
 
 - name
  
  Set the component name
  
 
 
 - logger
  
  Set the logger instance (``main::this_app`` is used as default when undefined)
  
 
 
 Optional arguments
 
 
 - config
  
  Set config as active config (using ``set_active_config`` method).
  
 
 



**************
Legacy methods
**************



- LogMessage
 
 Same as ``log`` method.
 This is deprecated, use ``log`` method instead.
 


- Report
 
 Same as ``report`` method.
 This is deprecated, use ``report`` method instead.
 


- Info
 
 Same as ``info`` method.
 This is deprecated, use ``info`` method instead.
 


- Verbose
 
 Same as ``verbose`` method.
 This is deprecated, use ``verbose`` method instead.
 


- Debug
 
 Similar to ``debug``,  but the debug level is set to 1.
 
 This is deprecated, use ``debug`` method instead and set loglevel.
 


- Warn
 
 Same as ``warn`` method.
 This is deprecated, use ``report`` method instead.
 


- Error
 
 Same as ``error`` method.
 This is deprecated, use ``error`` method instead.
 


