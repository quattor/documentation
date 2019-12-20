
#########################
EDG\::WP4\::CCM\::Options
#########################


****
NAME
****


EDG::WP4::CCM::Options


***********
DESCRIPTION
***********


Use this module to create (commandline) application that interact with CCM directly.

Available convenience methods:


- app_options
 
 Return list of CCM application specific options and
 commandline options for all CCM config options
 


- setCCMConfig
 
 Set the CCM Configuration instance for CID ``cid`` under CCM_CONFIG attribute
 using CacheManager's ``getConfiguration`` method.
 
 If ``cid`` is not defined, the ``cid`` value from the ``--cid``-option will be used.
 (To use the current CID when another cid value set via ``--cid``-option, pass an empty
 string or the string 'current').
 
 A CacheManager instance under CACHEMGR attribute is created if none exists
 or ``force_cache`` is set to true.
 
 Returns SUCCESS on success, undef on failure.
 


- getCCMConfig
 
 Returns the CCM configuration instance.
 If none exists, one is created via ``setCCMConfig`` method.
 
 All arguments are passed to possible ``setCCMConfig`` call.
 


- gatherPaths
 
 Retrun arrayref of selected profile path (via the PATH_SELECTION_METHODS)
 
 All options are treated as initial paths.
 


- default_action
 
 Set the default action ``$action`` if action is defined
 (use empty string to unset the default value).
 
 Returns the default action.
 


- action_showcids
 
 the showcids action prints all sorted profile CIDs as comma-separated list
 


- add_actions
 
 Add actions defined in hashref to the supported actions.
 
 When creating a new module derived from EDG::WP4::CCM::Options,
 add methods named "action_<something>", and add then via this method
 to the _actions hashref.
 
 This will create a commandline option "--something", if selected,
 will execute the action_<something> method.
 
 The hashref key is the action name, the value is the help text.
 
 (Returns the _actions hashref for unittesting purposes)
 


- action
 
 Run first of the predefined actions via the action_<actionname> methods
 


