
#########################
NCM\::Component\::systemd
#########################


****
NAME
****


NCM::systemd - NCM systemd component


*******
Methods
*******



- skip
 
 The ``skip`` methods determines what configuration work to skip.
 It returns a hashref with key the configuration name and a boolean
 value (to skip or not). Undefined configurations will be skipped.
 
 The main purpose for this method is to allow easy subclassing for
 replacement components.
 


- Configure()
 
 Configures ``systemd`` for each supported sub-system
 


