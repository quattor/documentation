
##########################
NCM\::Component\::iptables
##########################


****
NAME
****


iptables: Setup the IPTABLES firewall rules.


***********
DESCRIPTION
***********


The \ *IPTABLES*\  component perform the setup of the
``/etc/sysconfig/iptables`` configuration file and restarts the
iptables service.


********
SYNOPSIS
********



- Configure()
 
 This function apply the component resource declaration to the
 \ *IPTABLES*\  firewall tables.
 
 The \ *accept*\ , \ *drop*\ , \ *reject*\ , \ *return*\ , \ *classify*\  and \ *log*\ 
 default targets are supported.
 
 User defined targets are supported. We recommend that users specify new
 targets as a rule in the profile but the system will create them if it
 needs to - N.B. This means that you need to spell target names
 consistently and with identical capitalisation otherwise you will end up
 with multiple chains. E.g. chain "LocalRules" is not the same as
 "localrules".
 
 Duplicated entries in the component resource declaration are
 ignored. For each configured table, the chains are added to the
 ``/etc/sysconfig/iptables`` in order, the relative order among the rules
 belonging to the same chain is preserved.
 



*********
RESOURCES
*********


\* << `/software/components/iptables`>>
=======================================


Top component description with the following parameters:


.. code-block:: perl

   "filter"   ? component_iptables_acls
   "nat"      ? component_iptables_acls
   "mangle"   ? component_iptables_acls


These parameters correspond to the three \ *IPTABLES*\  table types.


\* type component_iptables_acls
===============================


The ``component_iptables_acls`` type is defined as:


.. code-block:: perl

   "preamble"      ? component_iptables_preamble
   "rules"         ? component_iptables_rule[]
   "epilogue"      ? string
   "ordered_rules" ? string with match (self, 'yes|no')


The ``epilogue`` parameter is the "COMMIT" command at the end of
\ *IPTABLES*\  table description. Presently, no check is performed upon
the content of this parameter.

If ``ordered_rules`` is set to yes, the ruleset will be written as
ordered in the original array. If set to no is is unset (the default),
the rules will be ordered by target type (first, all the "log" rules,
then "accept","drop", and "logging").


\* type component_iptables_preamble
===================================


The ``component_iptables_preamble`` type is defined as:


.. code-block:: perl

   "input"    ? string
   "output"   ? string
   "forward"  ? string


These parameters contain the global rules for stated rules,
e.g. ``:INPUT ACCEPT [0:0]``. Presently, no check is performed upon the
content of this parameters.


\* type component_iptables_rule
===============================


The ``component_iptables_rule`` type is defined as:


.. code-block:: perl

   "command"       ? string
   "chain"         : string
   "protocol"      ? string
   "src_addr"      ? string
   "src_port"      ? string
   "src_ports"     ? string
   "dst_addr"      ? string
   "dst_port"      ? string
   "dst_ports"     ? string
   "syn"           ? boolean
   "nosyn"         ? boolean
   "match"         ? string
   "state"         ? string
   "ctstate"       ? string
   "limit"         ? string
   "icmp_type"     ? string
   "in_interface"  ? string
   "out_interface" ? string
   "fragment"      ? boolean
   "nofragment"    ? boolean
   "target"        : string
   "reject-with"       ? string
   "log-prefix"        ? string
   "log-level"         ? string
   "log-tcp-options"   ? boolean
   "log-tcp-sequence"  ? boolean
   "log-ip-options"    ? boolean
   "set-class"     ? string
   "limit-burst"   ? number
   "length"        ? string
   "set"           ? boolean
   "rcheck"        ? boolean
   "seconds"       ? number



* The \ **"command"**\  defines the action to perform: "-A", "-D", "-I", "-N" or "-R", it defaults to "-A".



* The \ **"chain"**\  defines the chain: "input", "output" or "forward".



* The \ **"protocol"**\  defines the packet protocol: "tcp", "udp" or "icmp".



* The \ **"src_addr"**\  defines the packet source address, it can be an IP address, or a network in the form net/mask (CIDR notation or full mask), or a hostname (which will be resolved at configuration time, not at runtime) - all of which can be optionally prepended with "!" to negate the selection. To limit the ability of hackers/crackers to use your system for DDoS attacks it is worthwhile, for machines which are not being used as routers, to block packets which do not come from their IP address in the OUTPUT tables.



* The \ **"src_port"**\  defines the packet source port, it may be an integer or a service name included in the ``/etc/services`` file. This parameter requires \ **"protocol"**\  also be set.



* The \ **"dst_addr"**\  defines the packet destination address, it follows the same rules as the src_addr parameter.



* The \ **"dst_port"**\  defines the packet destination port, it follows the same rules as the src_port parameter. This parameter requires \ **"protocol"**\  also be set.



* The \ **"syn"**\  defines the TCP packet with the SYN bit set to one, it will be set if the parameter is true.



* The \ **"match"**\  defines the match extension module for the packet.



* The \ **"state"**\  defines the connection state.



* The \ **"limit"**\  defines the limit for logging.



* The \ **"limit-burst"**\  defines the number of instances per time step to record.



* The \ **"icmp_type"**\  defines the icmp type packet.



* The \ **"in_interface"**\  defines the input interface for the packet.



* The \ **"out_interface"**\  defines the output interface for the packet.



* The \ **"target"**\  defines the target for the packet: "log", "accept" or "drop".




\* function add_rule(<table>, <rule>)
=====================================


This function add a new entry rule to the resource list


.. code-block:: perl

     "/software/components/iptables/<table>/rules"




*****
FILES
*****


``/etc/sysconfig/iptables``:
================================


\ *IPTABLES*\  firewall configuration file policy.



********
EXAMPLES
********


Simple example
==============


The following is a code snippet from a node profile.
The lines have been numbered to aid the description.
This sets up IPTables and adds the necessary rules to restrict access
to SSH and allows all outgoing connections.


.. code-block:: perl

   1  "/software/components/iptables/active"                  = true;
   2  "/software/components/iptables/dispatch"                = default(true);
   3  "/software/components/iptables/dependencies/pre"        = list("spma");
   4  "/software/components/iptables/filter/preamble/input"   = "DROP [0:0]";
   5  "/software/components/iptables/filter/preamble/output"  = "ACCEPT [0:0]";
   6  "/software/components/iptables/filter/preamble/forward" = "DROP [0:0]";
   7 "/software/components/iptables/filter/epilogue"         = "COMMIT";
   8
   9 "/software/components/iptables/filter/rules" = append(nlist(
   10                        "command", "-A",
   11                        "chain", "input",
   12                        "target", "accept",
   13                        "match", "state",
   14                        "state", "ESTABLISHED"));
   15 "/software/components/iptables/filter/rules" = append(nlist(
   16                        "command", "-A",
   17                        "chain", "input",
   18                        "target", "accept",
   19                        "match", "state",
   20                        "state", "RELATED"));
   21 "/software/components/iptables/filter/rules" = append(nlist(
   22                        "command", "-A",
   23                        "chain", "input",
   24                        "target", "accept",
   25                        "match", "state",
   26                        "state", "NEW",
   27                        "protocol", "tcp",
   28                        "dst_port", "ssh"));



* Line 1 sets IPTables to be active and line 3 ensures that the software gets installed before the component tries to configure it.



* Lines 4-6 set the default policy for the input, output and forward chains. These can be set to either accept or drop. We don't recommend that you set these to log unless you have a very, very large disk. The COMMIT in line 7 is required by IPTables otherwise the rule set will be generated but not acted on.



* Lines 9 to 14 sets a rule to allow established connections.



* Lines 15 to 20 sets a rule to allow related connections. These are used by multi-threaded applications, such as SSH, which move the connection to a random port after authentication.



* Lines 21 to 28 creates a rule to allow the ssh service. The port number is set by the component querying ``/etc/services``. Alternatively you can specify the specific port number yourself.




Additional rules
================


DHCP
----



.. code-block:: perl

  "/software/components/iptables/filter/rules" = append(nlist(
                         "command", "-A",
                         "chain", "input",
                         "target", "accept",
                         "protocol", "udp",
                         "src_port", "67:68",
                         "dst_port", "67:68"));



NTP
---



.. code-block:: perl

  "/software/components/iptables/filter/rules" = append(nlist(
                         "command", "-A",
                         "chain", "input",
                         "target", "accept",
                         "protocol", "udp",
                         "src_port", "123",
                         "dst_port", "123"));



Samhain
-------



.. code-block:: perl

  "/software/components/iptables/filter/rules" = append(nlist(
                         "command", "-A",
                         "chain", "input",
                         "target", "accept",
                         "protocol", "tcp",
                         "src_port", "49777",
                         "dst_port", "49777"));



GridFTP Server
--------------



.. code-block:: perl

  "/software/components/iptables/filter/rules" = append(nlist(
                         "command", "-A",
                         "chain", "input",
                         "target", "accept",
                         "protocol", "tcp",
                         "dst_port", "2811"));