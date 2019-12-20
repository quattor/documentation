##############################
NCM\::Component\::cdp - schema
##############################

Types
-----

 - **/software/components/cdp/cdp_component**
    - */software/components/cdp/cdp_component/configFile*
        - Description: The location of the configuration file. Normally this should not be changed.
        - Required
        - Type: string
        - Default value: /etc/cdp-listend.conf
    - */software/components/cdp/cdp_component/port*
        - Description: The port used by the daemon.
        - Optional
        - Type: type_port
    - */software/components/cdp/cdp_component/nch*
        - Description: The binary to execute when receiving a CDB update packet.
        - Optional
        - Type: string
    - */software/components/cdp/cdp_component/nch_smear*
        - Description: The range of time delay for executing the nch executable. The execution will be delayed by [0, nch_smear] seconds.
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/cdp/cdp_component/fetch*
        - Description: The binary to execute when receiving a CCM update packet.
        - Optional
        - Type: string
    - */software/components/cdp/cdp_component/fetch_offset*
        - Description: Fetch execution offset. See explanation of fetch_smear.
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/cdp/cdp_component/fetch_smear*
        - Description: Fetch time smearing. The fetch binary will be started at a point in time between fetch_offset and fetch_offset + fetch_smear seconds after receiving a notification packet. The range of time delay for executing the fetch executable. The execution will be delayed by [0, fetch_smear] seconds.
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/cdp/cdp_component/hostname*
        - Optional
        - Type: type_hostname
