##########
types\::os
##########

Types
-----

 - **structure_os_version**
    - *structure_os_version/name*
        - Description: Descriptive form of version, e.g. 7x
        - Required
        - Type: string
    - *structure_os_version/major*
        - Description: Major version number component, e.g. 7
        - Optional
        - Type: long
        - Range: 0..
    - *structure_os_version/minor*
        - Description: Minor version number component
        - Optional
        - Type: long
        - Range: 0..
 - **structure_os_distribution**
    - *structure_os_distribution/name*
        - Description: Distribution name, e.g. sl
        - Required
        - Type: string
    - *structure_os_distribution/description*
        - Description: Full descriptive name, e.g. Scientific Linux
        - Optional
        - Type: string
    - *structure_os_distribution/family*
        - Description: Family that this distribution belongs to e.g. The family for "sl" would be "el"
        - Optional
        - Type: string
 - **structure_os**
    - *structure_os/distribution*
        - Description: OS distribution details
        - Required
        - Type: structure_os_distribution
    - *structure_os/version*
        - Description: OS version details
        - Required
        - Type: structure_os_version
    - *structure_os/architecture*
        - Description: Architecture of OS (may be different to system architecture)
        - Required
        - Type: cpu_architecture
