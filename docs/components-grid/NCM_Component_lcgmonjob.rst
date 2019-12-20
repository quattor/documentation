
###########################
NCM\::Component\::lcgmonjob
###########################


****
NAME
****


lcgmonjob: NCM component to configure lcg-mon-job-status daemon


***********
DESCRIPTION
***********


The \ *lcgmonjob*\  component manages the configuration for the
lcg-mon-job-status daemon.  It essentially just links the
init.d script to the correct location and ensures that the
daemon is restarted when the configuration changes.


*********
RESOURCES
*********


EDG_LOCATION
============


The location of the EDG software.


LCG_LOCATION
============


The location of the LCG software.


