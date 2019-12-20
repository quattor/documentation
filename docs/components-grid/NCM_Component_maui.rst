
######################
NCM\::Component\::maui
######################


****
NAME
****


maui: NCM component to configure Maui server.


***********
DESCRIPTION
***********


The \ *maui*\  component manages the configuration for the maui
scheduler. By default the configuration file resides in
`/var/spool/maui/maui.cfg`.


*********
RESOURCES
*********


configPath (/var/spool/maui)
============================


The absolute path for the maui configuration directory.


configFile (maui.cfg)
=====================


The file name for the maui configuration file.

contents
--------


The full contents of the maui configuration file.  The syntax is too
complex to fully translate into pan.  You must supply the complete
maui configuration file in this variable.



