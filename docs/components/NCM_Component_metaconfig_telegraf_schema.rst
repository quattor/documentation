################################################
NCM\::Component\::metaconfig\::telegraf - schema
################################################

Types
-----

 - **/software/components/metaconfig/telegraf_time_interval_string**
 - **/software/components/metaconfig/telegraf_file_size_string**
 - **/software/components/metaconfig/telegraf_global_tags**
 - **/software/components/metaconfig/telegraf_agent**
    - */software/components/metaconfig/telegraf_agent/interval*
        - Description: Default data collection interval for all inputs
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_agent/round_interval*
        - Description: Rounds collection interval to 'interval' ie, if interval="10s" then always collect on :00, :10, :20, etc.
        - Optional
        - Type: boolean
    - */software/components/metaconfig/telegraf_agent/metric_batch_size*
        - Description: Telegraf will send metrics to outputs in batches of at most metric_batch_size metrics. This controls the size of writes that Telegraf sends to output plugins.
        - Optional
        - Type: long
        - Range: 1..
    - */software/components/metaconfig/telegraf_agent/metric_buffer_limit*
        - Description: Maximum number of unwritten metrics per output. Increasing this value allows for longer periods of output downtime without dropping metrics at the cost of higher maximum memory usage.
        - Optional
        - Type: long
        - Range: 1..
    - */software/components/metaconfig/telegraf_agent/collection_jitter*
        - Description: Collection jitter is used to jitter the collection by a random amount. Each plugin will sleep for a random time within jitter before collecting. This can be used to avoid many plugins querying things like sysfs at the same time, which can have a measurable effect on the system.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_agent/flush_interval*
        - Description: Default flushing interval for all outputs. Maximum flush_interval will be flush_interval + flush_jitter
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_agent/flush_jitter*
        - Description: Jitter the flush interval by a random amount. This is primarily to avoid large write spikes for users running a large number of telegraf instances. ie, a jitter of 5s and interval 10s means flushes will happen every 10-15s
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_agent/precision*
        - Description: By default or when set to "0s", precision will be set to the same timestamp order as the collection interval, with the maximum being 1s. ie, when interval = "10s", precision will be "1s" when interval = "250ms", precision will be "1ms" Precision will NOT be used for service inputs. It is up to each individual service input to set the timestamp at the appropriate precision. Valid time units are "ns", "us" (or "µs"), "ms", "s".
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_agent/debug*
        - Description: Log at debug level.
        - Optional
        - Type: boolean
    - */software/components/metaconfig/telegraf_agent/quiet*
        - Description: Log only error level messages.
        - Optional
        - Type: boolean
    - */software/components/metaconfig/telegraf_agent/logtarget*
        - Description: Log target controls the destination for logs and can be one of "file", "stderr" or, on Windows, "eventlog". When set to "file", the output file is determined by the "logfile" setting.
        - Optional
        - Type: choice
    - */software/components/metaconfig/telegraf_agent/logfile*
        - Description: Name of the file to be logged to when using the "file" logtarget. If set to the empty string then logs are written to stderr.
        - Optional
        - Type: absolute_file_path
    - */software/components/metaconfig/telegraf_agent/logfile_rotation_interval*
        - Description: The logfile will be rotated after the time interval specified. When set to 0 no time based rotation is performed. Logs are rotated only when written to, if there is no log activity rotation may be delayed.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_agent/logfile_rotation_max_size*
        - Description: The logfile will be rotated when it becomes larger than the specified size. When set to 0 no size based rotation is performed.
        - Optional
        - Type: telegraf_file_size_string
    - */software/components/metaconfig/telegraf_agent/logfile_rotation_max_archives*
        - Description: Maximum number of rotated archives to keep, any older logs are deleted. If set to -1, no archives are removed.
        - Optional
        - Type: long
        - Range: -1..
    - */software/components/metaconfig/telegraf_agent/log_with_timezone*
        - Description: Pick a timezone to use when logging or type 'local' for local time. Example: America/Chicago
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_agent/hostname*
        - Description: Override default hostname, if empty use os.Hostname()
        - Optional
        - Type: type_hostname
    - */software/components/metaconfig/telegraf_agent/omit_hostname*
        - Description: If set to true, do no set the "host" tag in the telegraf agent.
        - Optional
        - Type: boolean
 - **/software/components/metaconfig/telegraf_plugin_common**
    - */software/components/metaconfig/telegraf_plugin_common/alias*
        - Description: Name an instance of a plugin.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/namepass*
        - Description: An array of glob pattern strings. Only metrics whose measurement name matches a pattern in this list are emitted.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/namedrop*
        - Description: The inverse of namepass. If a match is found the metric is discarded. This is tested on metrics after they have passed the namepass test.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/fieldpass*
        - Description: An array of glob pattern strings. Only fields whose field key matches a pattern in this list are emitted.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/fielddrop*
        - Description: The inverse of fieldpass. Fields with a field key matching one of the patterns will be discarded from the metric. This is tested on metrics after they have passed the fieldpass test.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/taginclude*
        - Description: An array of glob pattern strings. Only tags with a tag key matching one of the patterns are emitted. In contrast to tagpass, which will pass an entire metric based on its tag, taginclude removes all non matching tags from the metric. Any tag can be filtered including global tags and the agent host tag.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/tagexclude*
        - Description: The inverse of taginclude. Tags with a tag key matching one of the patterns will be discarded from the metric. Any tag can be filtered including global tags and the agent host tag.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/tagpass*
        - Description: A table mapping tag keys to arrays of glob pattern strings. Only metrics that contain a tag key in the table and a tag value matching one of its patterns is emitted.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_plugin_common/tagdrop*
        - Description: The inverse of tagpass. If a match is found the metric is discarded. This is tested on metrics after they have passed the tagpass test.
        - Optional
        - Type: string_trimmed
 - **/software/components/metaconfig/telegraf_iao_plugin_common**
    - */software/components/metaconfig/telegraf_iao_plugin_common/name_override*
        - Description: Override the base name of the measurement. (Default is the name of the input).
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_iao_plugin_common/name_prefix*
        - Description: Specifies a prefix to attach to the measurement name.
        - Optional
        - Type: string_trimmed
    - */software/components/metaconfig/telegraf_iao_plugin_common/name_suffix*
        - Description: Specifies a suffix to attach to the measurement name.
        - Optional
        - Type: string_trimmed
 - **/software/components/metaconfig/telegraf_plugin_input**
    - */software/components/metaconfig/telegraf_plugin_input/interval*
        - Description: Overrides the interval setting of the agent for the plugin. How often to gather this metric. Normal plugins use a single global interval, but if one particular input should be run less or more often, you can configure that here.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_input/precision*
        - Description: Overrides the precision setting of the agent for the plugin. Collected metrics are rounded to the precision specified as an interval. When this value is set on a service input, multiple events occuring at the same timestamp may be merged by the output database.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_input/collection_jitter*
        - Description: Overrides the collection_jitter setting of the agent for the plugin. Collection jitter is used to jitter the collection by a random interval.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_input/tags*
        - Description: A map of tags to apply to a specific input's measurements.
        - Optional
        - Type: string_trimmed
 - **/software/components/metaconfig/telegraf_plugin_output**
    - */software/components/metaconfig/telegraf_plugin_output/flush_interval*
        - Description: The maximum time between flushes. Use this setting to override the agent flush_interval on a per plugin basis.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_output/flush_jitter*
        - Description: The amount of time to jitter the flush interval. Use this setting to override the agent flush_jitter on a per plugin basis.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_output/metric_batch_size*
        - Description: The maximum number of metrics to send at once. Use this setting to override the agent metric_batch_size on a per plugin basis.
        - Optional
        - Type: long
        - Range: 1..
    - */software/components/metaconfig/telegraf_plugin_output/metric_buffer_limit*
        - Description: The maximum number of unsent metrics to buffer. Use this setting to override the agent metric_buffer_limit on a per plugin basis.
        - Optional
        - Type: long
        - Range: 1..
 - **/software/components/metaconfig/telegraf_plugin_processor**
    - */software/components/metaconfig/telegraf_plugin_processor/order*
        - Description: The order in which the processor(s) are executed. If this is not specified then processor execution order will be random.
        - Optional
        - Type: long
        - Range: 1..
 - **/software/components/metaconfig/telegraf_plugin_aggregator**
    - */software/components/metaconfig/telegraf_plugin_aggregator/period*
        - Description: The period on which to flush & clear each aggregator. All metrics that are sent with timestamps outside of this period will be ignored by the aggregator.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_aggregator/delay*
        - Description: The delay before each aggregator is flushed. This is to control how long for aggregators to wait before receiving metrics from input plugins, in the case that aggregators are flushing and inputs are gathering on the same interval.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_aggregator/grace*
        - Description: The duration when the metrics will still be aggregated by the plugin, even though they're outside of the aggregation period. This is needed in a situation when the agent is expected to receive late metrics and it's acceptable to roll them up into next aggregation period.
        - Optional
        - Type: telegraf_time_interval_string
    - */software/components/metaconfig/telegraf_plugin_aggregator/drop_original*
        - Description: If true, the original metric will be dropped by the aggregator and will not get sent to the output plugins.
        - Optional
        - Type: boolean
    - */software/components/metaconfig/telegraf_plugin_aggregator/tags*
        - Description: A map of tags to apply to the measurement - behavior varies based on aggregator.
        - Optional
        - Type: string_trimmed
 - **/software/components/metaconfig/service_telegraf**
    - */software/components/metaconfig/service_telegraf/global_tags*
        - Optional
        - Type: telegraf_global_tags
    - */software/components/metaconfig/service_telegraf/agent*
        - Optional
        - Type: telegraf_agent
    - */software/components/metaconfig/service_telegraf/inputs*
        - Optional
        - Type: telegraf_plugin_input
    - */software/components/metaconfig/service_telegraf/processors*
        - Optional
        - Type: telegraf_plugin_processor
    - */software/components/metaconfig/service_telegraf/aggregators*
        - Optional
        - Type: telegraf_plugin_aggregator
    - */software/components/metaconfig/service_telegraf/outputs*
        - Optional
        - Type: telegraf_plugin_output
