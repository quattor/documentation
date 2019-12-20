#####################################
NCM\::Component\::spma\::apt - schema
#####################################

Types
-----

 - **/software/components/spma/component_spma_apt**
    - */software/components/spma/component_spma_apt/userrepos*
        - Description: Allow user defined (i.e. unmanaged) repositories to be present on the system
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/spma/component_spma_apt/userpkgs*
        - Description: Allow user installed (i.e. unmanaged) packages to be present on the system
        - Required
        - Type: boolean
        - Default value: false
