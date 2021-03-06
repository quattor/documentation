####################################
NCM\::Component\::pbsclient - schema
####################################

Types
-----

 - **/software/components/pbsclient/pbsclient_component_pathmapping_type**
    - */software/components/pbsclient/pbsclient_component_pathmapping_type/locations*
        - Required
        - Type: string
    - */software/components/pbsclient/pbsclient_component_pathmapping_type/path*
        - Required
        - Type: string
 - **/software/components/pbsclient/pbsclient_component_scripts_type**
    - */software/components/pbsclient/pbsclient_component_scripts_type/epilogue*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_scripts_type/epilogue.user*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_scripts_type/epilogue.parallel*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_scripts_type/prologue*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_scripts_type/prologue.user*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_scripts_type/prologue.parallel*
        - Optional
        - Type: string
 - **/software/components/pbsclient/pbsclient_component_structure_initialisation**
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/auto_ideal_load*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/auto_max_load*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/check_poll_time*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/checkpoint_interval*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/checkpoint_script*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/checkpoint_run_exe*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/configversion*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/cputmult*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/down_on_error*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/enablemomrestart*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/ideal_load*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/igncput*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/ignmem*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/ignvmem*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/ignwalltime*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/job_output_file_mask*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/log_directory*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/logevent*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/log_file_suffix*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/log_keep_days*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/loglevel*
        - Optional
        - Type: long
        - Range: 0..7
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/log_file_max_size*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/log_file_roll_depth*
        - Optional
        - Type: long
        - Range: 1..
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/max_conn_timeout_micro_sec*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/max_load*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/memory_pressure_threshold*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/memory_pressure_duration*
        - Optional
        - Type: long
        - Range: 0..
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/node_check_script*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/node_check_interval*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/nodefile_suffix*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/nospool_dir_list*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/job_oom_score_adjust*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/prologalarm*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/rcpcmd*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/remote_checkpoint_dirs*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/remote_reconfig*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/restart_script*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/source_login_batch*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/source_login_interactive*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/spool_as_final_name*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/status_update_time*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/tmpdir*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/timeout*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/use_smt*
        - Optional
        - Type: boolean
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/wallmult*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/cpuTimeMultFactor*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/idealLoad*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/logEvent*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/maxLoad*
        - Optional
        - Type: double
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/nodeCheckScriptPath*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/nodeCheckIntervalSec*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/prologAlarmSec*
        - Optional
        - Type: long
    - */software/components/pbsclient/pbsclient_component_structure_initialisation/wallTimeMultFactor*
        - Optional
        - Type: double
 - **/software/components/pbsclient/pbsclient_component_structure_options**
    - */software/components/pbsclient/pbsclient_component_structure_options/mom_host*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_structure_options/xauthpath*
        - Optional
        - Type: string
 - **/software/components/pbsclient/pbsclient_component_type**
    - */software/components/pbsclient/pbsclient_component_type/pbsroot*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/configPath*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/initScriptPath*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/behaviour*
        - Optional
        - Type: string
        - Default value: OpenPBS
    - */software/components/pbsclient/pbsclient_component_type/masters*
        - Required
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/pbsclient*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/aliases*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/restricted*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/cpuinfo*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/varattr*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/resources*
        - Optional
        - Type: string
    - */software/components/pbsclient/pbsclient_component_type/directPaths*
        - Optional
        - Type: pbsclient_component_pathmapping_type
    - */software/components/pbsclient/pbsclient_component_type/scripts*
        - Optional
        - Type: pbsclient_component_scripts_type
    - */software/components/pbsclient/pbsclient_component_type/submitonly*
        - Optional
        - Type: boolean
