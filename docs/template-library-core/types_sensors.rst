###############
types\::sensors
###############

Types
-----

 - **structure_sensor**
    - *structure_sensor/name*
        - Required
        - Type: string_trimmed
    - *structure_sensor/threshold*
        - Required
        - Type: long
    - *structure_sensor/unit*
        - Required
        - Type: string_non_whitespace
 - **structure_sensor_temperature**
    - *structure_sensor_temperature/unit*
        - Required
        - Type: string
        - Default value: C
 - **structure_sensor_voltage**
    - *structure_sensor_voltage/unit*
        - Required
        - Type: string
        - Default value: V
 - **structure_sensor_current**
    - *structure_sensor_current/unit*
        - Required
        - Type: string
        - Default value: A
 - **structure_sensor_power**
    - *structure_sensor_power/unit*
        - Required
        - Type: string
        - Default value: W
 - **structure_sensor_fanspeed**
    - *structure_sensor_fanspeed/unit*
        - Required
        - Type: string
        - Default value: RPM
 - **structure_sensor_types**
    - *structure_sensor_types/temperature*
        - Optional
        - Type: structure_sensor_temperature
    - *structure_sensor_types/voltage*
        - Optional
        - Type: structure_sensor_voltage
    - *structure_sensor_types/current*
        - Optional
        - Type: structure_sensor_current
    - *structure_sensor_types/power*
        - Optional
        - Type: structure_sensor_power
    - *structure_sensor_types/fanspeed*
        - Optional
        - Type: structure_sensor_fanspeed
