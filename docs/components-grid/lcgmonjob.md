
### NAME

lcgmonjob: NCM component to configure lcg-mon-job-status daemon

### DESCRIPTION

The _lcgmonjob_ component manages the configuration for the
lcg-mon-job-status daemon.  It essentially just links the
init.d script to the correct location and ensures that the
daemon is restarted when the configuration changes.

### RESOURCES

#### EDG\_LOCATION

The location of the EDG software.

#### LCG\_LOCATION

The location of the LCG software.
