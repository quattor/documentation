###################################
NCM\::Component\::filecopy - schema
###################################

Types
-----

 - **/software/components/filecopy/structure_filecopy**
    - */software/components/filecopy/structure_filecopy/config*
        - Description: The file content specified as a string.
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/source*
        - Description: The name of a source file already present on the machine to use as the content for the managed file.
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/restart*
        - Description: A command to execute if the file is modified. It is typically used to restart a service but any valid command can be specified, including several commands separated by ';'. If not specified, the file is updated but no command is executed. Restart commands are executed after all files have been updated. If several files specify the same restart command, it is executed once.
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/perms*
        - Description: Permissions of the managed file. If not specified, the default permissions on the system will be used.
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/owner*
        - Description: The userid of the file owner. It can also be a 'user:group' specification (like with chown).
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/group*
        - Description: The group of the file owner. It is ignored if the owner is specified as 'user:group'.
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/no_utf8*
        - Description: By default, the file content is converted to UTF8. Define this property to 'true' to prevent this conversion.
        - Optional
        - Type: boolean
    - */software/components/filecopy/structure_filecopy/forceRestart*
        - Description: A boolean that defines if the restart command (if any defined). must be executed even though the file was up-to-date (default behaviour is to execute the restart command only if file content, permissions or owner/group has been changed). Note: this attribute is ignored if the global 'forceRestart' value is true.
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/filecopy/structure_filecopy/backup*
        - Description: This property specifies if an existing version of the file must be backed up before being updated (backup extension is '.old').
        - Required
        - Type: boolean
        - Default value: true
 - **/software/components/filecopy/component_filecopy**
    - */software/components/filecopy/component_filecopy/services*
        - Description: This dict contains one entry by file to manage. The key is the escaped file name. For each file, the property described below may be specified. Most properties are optional (or have a default value) but either 'config' or 'source' MUST be specified and they are mutually exclusive.
        - Optional
        - Type: structure_filecopy
    - */software/components/filecopy/component_filecopy/forceRestart*
        - Description: A boolean that defines if the restart command (if any defined) of the file(s) must be executed even though the files were up-to-date (default behaviour is to execute the restart command only if file content, permissions or owner/group has been changed).
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/filecopy/component_filecopy/ignore_restart_failure*
        - Description: A boolean that defines if failures of restart command should be regarded as fatal or not.
        - Optional
        - Type: boolean

Functions
---------

 - component_filecopy_valid
