
####################
NCD\::ComponentProxy
####################


****
NAME
****


NCD::ComponentProxy - component proxy class


***********
INHERITANCE
***********



.. code-block:: perl

   CAF::Object, CAF::Reporter



***********
DESCRIPTION
***********


Provides management functions for accessing and executing NCM
components.

Public methods
==============



- executeConfigure
 
 executeConfigure loads and executes the component with ``Configure`` method.
 The number of produced errors and warnings is returned in
 a hashref with keys ``ERRORS`` and ``WARNINGS``.
 If the component cannot be executed, undef is returned.
 


- executeUnconfigure
 
 executeUnconfigure loads and executes the component with ``Unconfigure``.
 The number of produced errors and warnings is returned in
 a hashref with keys ``ERRORS`` and ``WARNINGS``.
 If the component cannot be executed, undef is returned.
 


- name
 
 returns the name of the component
 


- module
 
 returns the module to be loaded for executing the component
 


- getPreDependencies
 
 returns an arrayref with the names of predependent components.
 The arrayref is empty if no predependencies are found.
 


- getPostDependencies
 
 returns an arrayref with the names of postdependent components.
 The array is empty if no postdependencies are found.
 


- _getComponentFilename
 
 Returns the absolute filename of a loaded component module.
 



Private methods
===============



- _initialize
 
 object initialization (done via new)
 


- _load
 
 Load the component file in a separate namespace ``NCM::Component::<name>``
 
 Returns the component instance on success, undef on failure.
 


- _setDependencies
 
 Reads the dependencies on other components via the NVA API and stores
 them internally. They can be recovered by getDependencies()
 


- _version_check
 
 Apply version related checks.
 
 Return ``SUCCESS`` if there are no version-related issues;
 report an error and return undef otherwise.
 
 Current version only reports possible different versions,
 and always returns ``SUCCESS``
 (but behaviour might change in future versions).
 


- _execute
 
 common function for executeConfigure() and executeUnconfigure()
 
 Adds the ``USR1`` signal handler (reports the (currently active) component and method)
 ``HUP``, ``PIPE`` and ``ALRM`` signals are ignored during the method execution.
 



