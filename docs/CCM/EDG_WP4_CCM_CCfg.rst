
######################
EDG\::WP4\::CCM\::CCfg
######################


****
NAME
****


EDG::WP4::CCM::CCfg


********
SYNOPSIS
********



.. code-block:: perl

   init()
     or
   init("/etc/ccm.conf")
 
   $cache_root = getCfgValue ("cache_root");



***********
DESCRIPTION
***********


CCfg is used to get configuration parameters. Defualt values for
configuration parameters get overwritten if defined in configuration
file.


- initCfg (;$cfg_file)
 
 Initialise CCfg. if $cfg_file parameter is present, file has to exists,
 if it does not exist error is risen. If the parameter is not present
 defualt EDG paths are used. If configuration file does not exist in defualt
 locations the default values are used.
 


- getCfgValue ($key)
 
 returns a value of the configuration parameter identified by $key.
 


- setCfgValue ($key, $value, $force)
 
 Set the configuration option ``$key`` to ``$value``.
 If force is set, the option and value are also added
 to the ``force_cfg`` hashref, making it protected against
 rereading of the config file.
 


- resetCfg
 
 reset the configuration hash and empty the force
 hashref.
 


