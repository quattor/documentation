
### Types

 - `/software/cron/structure_cron_syslog`
    - `/software/cron/structure_cron_syslog/facility`
        - Optional
        - Type: string
        - Default value: user
    - `/software/cron/structure_cron_syslog/level`
        - Optional
        - Type: string
        - Default value: notice
    - `/software/cron/structure_cron_syslog/tagprefix`
        - Optional
        - Type: string
        - Default value: ncm-cron.
    - `/software/cron/structure_cron_syslog/tag`
        - Optional
        - Type: string
 - `/software/cron/structure_cron_log`
    - Description:
    Define specific attributes for cron log file.

    - `/software/cron/structure_cron_log/disabled`
        - Description: A boolean disabling the redirection of script output/error to a log file
        - Optional
        - Type: boolean
    - `/software/cron/structure_cron_log/name`
        - Description: Name of the log file. If the name is not an absolute file name, file is created in /var/log.
    Default name is the cron filename with .log extension in /var/log.
        - Optional
        - Type: string
    - `/software/cron/structure_cron_log/owner`
        - Description: Owner/group of the log file, using owner[:group] format. Group can be ommitted.
        - Optional
        - Type: string
    - `/software/cron/structure_cron_log/mode`
        - Description: Permissions of log file specified as a string interpreted as an octal number.
        - Optional
        - Type: string
 - `/software/cron/structure_cron_timing`
    - `/software/cron/structure_cron_timing/minute`
        - Optional
        - Type: string
    - `/software/cron/structure_cron_timing/hour`
        - Optional
        - Type: string
    - `/software/cron/structure_cron_timing/day`
        - Optional
        - Type: string
    - `/software/cron/structure_cron_timing/month`
        - Optional
        - Type: string
    - `/software/cron/structure_cron_timing/weekday`
        - Optional
        - Type: string
    - `/software/cron/structure_cron_timing/smear`
        - Optional
        - Type: long
        - Range: 0..1440
 - `/software/cron/structure_cron`
    - `/software/cron/structure_cron/name`
        - Description: Filename (without suffix) of the cron entry file to create.
        - Optional
        - Type: string
    - `/software/cron/structure_cron/user`
        - Description: User to use to run the command. Defaults to root if none defined
        - Optional
        - Type: string
    - `/software/cron/structure_cron/group`
        - Description: Group to use to run the command. Defaults to user's primary group.
        - Optional
        - Type: string
    - `/software/cron/structure_cron/frequency`
        - Description: Execution frequency for the command, using standard cron syntax.
      Minutes field can be 'AUTO :' in which case,
      a random value between 0 and 59 inclusive is generated.
      This can be used to avoid too many machines executing the same
      cron at the same time. See also the C<timing> element.
        - Optional
        - Type: string
    - `/software/cron/structure_cron/timing`
        - Description: If the 'timing' dict is used to specify the time, it can contain any of the
      keys: 'minute', 'hour', 'day', 'month' and 'weekday'. An unspecified key will
      have a value of '*'. A further key of 'smear' can be used to specify (in
      minutes) a maximum interval for smearing the start time, which can be as much
      as a day. When a smeared job is created, a random increment between zero and
      the smear time is applied to the start time of the job.  If the start time
      results in the job running on the following day, then all other fields (day,
      weekday, etc) will be suitably modified. When smearing is specified, then the
      start minute (and possibly hour, if smear is more than one hour) must be
      specified as a simple absolute (e.g. '2') and cannot be variations such as
      lists or ranges.  Time specifications such as ranges, lists and steps are
      supported except for named values (e.g. "1" must be used instead of "mon").
        - Optional
        - Type: structure_cron_timing
    - `/software/cron/structure_cron/command`
        - Description: Command line to execute, including all its options.
        - Optional
        - Type: string
    - `/software/cron/structure_cron/comment`
        - Description: An optional comment to add at the beginning of the cron file.
        - Optional
        - Type: string
    - `/software/cron/structure_cron/env`
        - Description: An optional dict containing environment variable that must be
      defined before executing the command. Key is
      the variable name, value is variable value.
        - Optional
        - Type: string
    - `/software/cron/structure_cron/log`
        - Optional
        - Type: structure_cron_log
    - `/software/cron/structure_cron/syslog`
        - Optional
        - Type: structure_cron_syslog
 - `/software/cron/cron_component`
    - `/software/cron/cron_component/entries`
        - Description: A list containing cron structures (described above).
        - Optional
        - Type: structure_cron
    - `/software/cron/cron_component/deny`
        - Optional
        - Type: string
    - `/software/cron/cron_component/allow`
        - Optional
        - Type: string
    - `/software/cron/cron_component/securitypath`
        - Optional
        - Type: string
        - Default value: /etc

### Functions

 - structure_cron_log_valid
    - Description:
    Function to check that other log properties are not present when disabled is true

