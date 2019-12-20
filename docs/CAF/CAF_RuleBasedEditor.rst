
#####################
CAF\::RuleBasedEditor
#####################


***********
DESCRIPTION
***********


This module implements a rule-based editor that is used to modify the content
of an existing file. Each rule driving the editing process is applied to all
lines wose "keyword" is matching the one specified in the rule. The input for
updating the file is a hash typically built from the Quattor configuration when
the rule-based editor is called from a configuration module. Conditions can be defined
based on the contents of this configuration. Lines in the configuration file
that don't match any rule are kept unmodified.

This module is a subclass of the \ **CAF::FileEditor**\ : it extends the base methods of
the \ **CAF::FileEditor**\ . It has only one public method (it uses the \ **CAF::FileEditor**\  constructor).
The methods provided in this module can be combined with \ **CAF::FileEditor**\ 
methods to edit a file.

Rules used to edit the file are defined in a hash: each entry (key/value pair) defines a rule.
Multiple rules can be applied to the same file: it is important that they are
orthogonal, else the result is unpredictable. The order used to apply rules is the alphabetical
order of keywords. Applying the rules to the same configuration always give the same result
but the changes are not necessarily idempotent (order in which successive edits occured
may matter, depending on the actual rules).

The hash entry key represents the line keyword in configuration file and
hash value is the parsing rule for the keyword value. Parsing rule format is :


.. code-block:: perl

       [condition->]option_name:option_set[,option_set,...];line_fmt[;value_fmt[:value_fmt_opt]]


If the line keyword (hash key) starts with a '-', the matching
configuration line will be removed/commented out (instead of added/updated) from the
configuration file if present. If it starts with a '?', the
matching line will be removed/commented out if the option is undefined.


- condition
 
 An option or an option set/subset (see below) that must exist for the rule to be applied
 or the keyword ``ALWAYS``.
 Both ``option_set`` and ``option_name:option_set`` are accepted. option and option set
 in the condition are normally different from the ``option_name`` and ``option_set``
 parameters in the rule as this is the default behaviour to apply the rule only if
 they exist. One option set only is allowed and only its existence (not its value) is tested.
 
 ``option_set`` can be either an actual option set as defined below or a subset of an option set
 (a subhash of the option set hash). To specify a subset, use ``/`` as a level separator,
 e.g. ``xroot/securityProtocol/gsi`` (``gsi`` subet of ``securityProtocol`` subset of ``xroot`` option set).
 
 It is possible to negate the condition (option or option_set must not exist)
 by prepending it with '!'.
 
 ``ALWAYS`` is a special condition that means that rules must be applied whether
 the ``option_name:option_set`` exist in the configuration or not. When they don't exist
 the result is to comment out the matching configuration lines.
 


- option_name
 
 The name of an option that will be retrieved from the configuration. An option is
 a key in the option set hash.
 


- option_set
 
 The name of an option set where the option is located in (for example 'dpnsHost:dpm'
 means ``dpnsHost`` option of ``dpm`` option set). An option set is a sub-hash in the configuration
 hash. ``GLOBAL`` is a special value for ``option_set`` indicating that the option is a global option,
 instead of belonging to a specific option set (global options are at the top level of the configuration
 hash).
 


- line_fmt
 
 Defines the format used to represent the keyword/value pair. Several format are supported covering
 the most usual ones (SH shell script, Apache, ...). For the exact list, see the definition of
 LINE_FORMAT_xxx constants and the associated documentation below.
 


- value_fmt
 
 used to indicate how to interpret the configuration value. It is used mainly for
 boolean values, list and hashes. See LINE_VALUE_xxx constants below for the possible values.
 


- value_fmt
 
 used to indicate how to interpret the configuration value. It is used mainly for
 boolean values, list and hashes. See LINE_VALUE_xxx constants below for the possible values.
 


An example of rule declaration is:


.. code-block:: perl

     my %dpm_config_rules_2 = (
         "ALLOW_COREDUMP" => "allowCoreDump:dpm;".LINE_FORMAT_SH_VAR.";".LINE_VALUE_BOOLEAN,
         "GLOBUS_THREAD_MODEL" => "globusThreadModel:dpm;".LINE_FORMAT_ENV_VAR,
         "DISKFLAGS" =>"DiskFlags:dpm;".LINE_FORMAT_SH_VAR.";".LINE_VALUE_ARRAY,
        );


For more comprehensive examples of rules, look at \ **ncm-dpmlfc**\  or \ **ncm-xrootd**\  source code in
configuration-modules-grid repository.

Rule Constants
==============


The constants described here are used to build the rules. All these
constants are exported. Add the following to use them:


.. code-block:: perl

     use RuleBasedEditor qw(:rule_constants);


There is a different group of constants for each part of the rule.

LINE_FORMAT_xxx: general syntax of the line
-------------------------------------------



- LINE_FORMAT_KW_VAL
 
 Keyword value (e.g. Xrootd, Apache) keywork/value separator can be customized with ``LINE_VALUE_OPT_SEP_xxx``. No coment is added to the line.
 This is the default line format.
 


- LINE_FORMAT_KW_VAL_SET
 
 Set keyword value. Same remarks as for LINE_FORMAT_KW_VAL.
 


- LINE_FORMAT_KW_VAL_SETENV
 
 Setenv keyword value Same remarks as for LINE_FORMAT_KW_VAL.
 


- LINE_FORMAT_ENV_VAR
 
 Export keyword=value (e.g. SH shell family). A comment is added at the end of the line if it
 is modified by \ **CAF::RuleBasedEditor**\ . If the value contains whitespaces, it is quoted.
 


- LINE_FORMAT_SH_VAR
 
 keyword=value (e.g. SH shell family). A comment is added at the end of the line if it is modified by \ **CAF::RuleBasedEditor**\ .
 If the value contains whitespaces, it is quoted.
 


Inline comments are not supported for the LINE_FORMAT_KW_VAL_xxx formats.


LINE_VALUE_xxx: how to interpret the configuration value
--------------------------------------------------------



- LINE_VALUE_AS_IS
 
 Take the value as it is, do not attempt any conversion. This is the default value type.
 


- LINE_VALUE_BOOLEAN
 
 Interpret the value as a boolean rendered as ``yes`` or ``no``.
 


- LINE_VALUE_ARRAY
 
 The value is an array. Rendering controlled by LINE_OPT_xxx constants.
 


- LINE_VALUE_HASH
 
 The value is a hash of strings. Rendering controlled by LINE_OPT_xxx constants.
 


- LINE_VALUE_HASH_KEYS
 
 The value is a hash whose keys are the value. Rendering similar to arrays with
 ``LINE_VALUE_ARRAY`` (the key list is treated as an array).
 


- LINE_VALUE_INSTANCE_PARAMS
 
 specific to \ **ncm-xrootd**\ 
 



LINE_OPT_xxx: options for rendering the config line
---------------------------------------------------


These options mainly apply to lists and hashes and are interpreted as a bitmask.


- LINE_OPT_KEY_PREFIX_DASH
 
 If set, add a ``-`` before the keyword when writing it in the configuration file.
 


- LINE_OPT_VALUE_ONELINE
 
 Each value in an array or keyword/value pair in a hash must be on a separate line. This results in
 several instances of the same keyword (multiple lines) in the configuration file.
 


- LINE_OPT_VALUE_UNIQUE
 
 Each values are concatenated as a space-separated string
 


- LINE_OPT_VALUE_SORTED
 
 Values are sorted
 


- LINE_OPT_HASH_SEP_COLON
 
 When LINE_VALUE_HASH, use a colon between each hash key and value.
 


- LINE_OPT_SEP_COLON
 
 Use a colon between keyword and value.
 


- LINE_OPT_SEP_EQUAL
 
 Use an equal sign between keyword and value.
 


- LINE_VALUE_OPT_SPACE_AROUND_SEP
 
 When updating the value, put a space around the keyword/value separator.
 


$FILE_INTRO_xxx: constants defining the expected header lines in the configuration file



Public methods
==============



- updateFile
 
 Update configuration file contents,  applying configuration rules.
 
 Arguments :
 
 
 .. code-block:: perl
 
      config_rules: a hashref containing config rules corresponding to the file to build
      config_options: a hashref for configuration parameters used to build actual configuration
      options: a hashref defining options to modify the behaviour of this function
 
 
 Supported entries for options hash:
 
 
 .. code-block:: perl
 
      always_rules_only: if true, apply only rules with ALWAYS condition (D: false). See introduction
                         about the ALWAYS condition.
      remove_if_undef: if true, remove matching configuration line if rule condition is not met (D: false)
 
 
 Return value
 
 
 .. code-block:: perl
 
      sucess: 1
      error processing of one or more rules: 0
      argument error or error duing rule processing: undef
 
 



Private methods
===============



- formatAttributeValue
 
 This function formats an attribute value based on the value format specified.
 
 Arguments:
 
 
 .. code-block:: perl
 
      attr_value : attribute value (type interpreted based on C<value_fmt>)
      line_fmt : line format (see LINE_FORMAT_xxx constants)
      value_fmt : value format (see LINE_VALUE_xxx constants)
      line_opt: line rendering options
 
 
 Return value:
 
 
 .. code-block:: perl
 
      A string corresponding to the value formatted according to the format specified by arguments
      or undef in case of an internal error (missing arguments)
 
 


- _formatConfigLine
 
 This function formats a configuration line using keyword and value,
 according to the line format requested. Values containing spaces are
 quoted if the line format is not LINE_FORMAT_KW_VAL.
 
 Arguments :
 
 
 .. code-block:: perl
 
      keyword : line keyword
      value : keyword value (can be an empty string)
      line_fmt : line format (see LINE_FORMAT_xxx constants)
      line_opt: line rendering options
 
 
 Return value:
 
 
 .. code-block:: perl
 
      A string corresponding to the line formatted according to line_fmt
      or undef in case of an internal error (missing arguments)
 
 


- _escape_regexp_string
 
 Help method to escape all characters with a special interpretation in the context
 of a regexp.
 
 Arguments:
 
 
 .. code-block:: perl
 
      regexp_str: initial regexp string (characters not escaped)
 
 
 Return value:
 
 
 .. code-block:: perl
 
      string: regexp with all specail characters escaped
 
 


- _buildLinePattern
 
 This function builds a pattern that will match an existing configuration line for
 the configuration parameter specified. The pattern built takes into account the line format.
 Every whitespace in the pattern (configuration parameter) are replaced by \s+.
 If the line format is LINE_FORMAT_KW_VAL, no whitespace is
 imposed at the end of the pattern, as this format can be used to write a configuration
 directive as a keyword with no value.
 
 Arguments :
 
 
 .. code-block:: perl
 
      config_param: parameter to update
      line_fmt: line format (see LINE_FORMAT_xxx constants)
      line_opt: line rendering options
      config_value: when defined, make it part of the pattern (used when multiple lines
                    with the same keyword are allowed)
 
 
 Return value:
 
 
 .. code-block:: perl
 
      A string containing the pattern to use to match the line in the file or undef
      in case of an internal error (missing argument or an invalid line format).
 
 


- _commentConfigLine
 
 This function comments out a configuration line matching the configuration parameter.
 Match operation takes into account the line format.
 
 Arguments :
 
 
 .. code-block:: perl
 
      config_param: parameter to update
      line_fmt : line format (see LINE_FORMAT_xxx constants)
      line_opt: line rendering options
 
 
 Return value:
 
 
 .. code-block:: perl
 
      success: 1
      error during processing: 0
      internal error (missing argument): undef
 
 


- _updateConfigLine
 
 This function does the actual update of a configuration line after doing the final
 line formatting based on the line format.
 
 Arguments :
 
 
 .. code-block:: perl
 
      config_param: parameter to update
      config_value: parameter value (can be an empty string)
      line_fmt: line format (see LINE_FORMAT_xxx constants)
      line_opt: line rendering options
      multiple: if true, multiple lines with the same keyword can exist (D: false)
 
 
 Return value:
 
 
 .. code-block:: perl
 
      undef or 1 in case of an internal error (missing argument)
 
 


- _parse_rule
 
 Parse a rule and return as a hash the information necessary to edit lines. If the rule
 condition is not met, undef is returned. If an error occured, the hash contains more
 information about the error.
 
 Arguments :
 
 
 .. code-block:: perl
 
      rule: rule to parse
      config_options: configuration parameters used to build actual configuration
      parser_options: a hashref defining options to modify the behaviour of this function
 
 
 Supported entries for options hash:
 
 
 .. code-block:: perl
 
      always_rules_only: if true, apply only rules with ALWAYS condition (D: false). See introduction
                         about the ALWAYS condition.
      remove_if_undef: if true, remove matching configuration line if rule condition is not met (D: false)
 
 
 Return value: undef if the rule condition is not met or a hash with the following information:
 
 
 .. code-block:: perl
 
      error_msg: a non empty string if an error happened during parsing
      remove_matching_lines: a boolean indicating that the matching lines must be removed
      option_sets: a list of option sets containing the attribute to use in the updated line
      attribute: the option attribute to use in the updated line
 
 


- _apply_rules
 
 Apply configuration rules. This method is the real workhorse of the rule-based editor.
 
 Arguments :
 
 
 .. code-block:: perl
 
      config_rules: config rules corresponding to the file to build
      config_options: configuration parameters used to build actual configuration. Note that keys in the
                      config_options hash are interpreted as escaped (generally harmless if they are not as the
                      killing sequence, '_'+ 2 hex digit, is unlikely to occur in this context. Use camel case
                      for keys to prevent problems).
      parser_options: a hash setting options to modify the behaviour of this function
 
 
 Supported entries for options hash:
 
 
 .. code-block:: perl
 
      always_rules_only: if true, apply only rules with ALWAYS condition (D: false)
      remove_if_undef: if true, remove matching configuration line if rule condition is not met (D: false)
 
 
 Return value:
 
 
 .. code-block:: perl
 
      success: 1
      error processing one or more rules: 0
      undef in case of an internal error (missing argument)
 
 



