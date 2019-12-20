
############################
NCM\::Component\::authconfig
############################


****
NAME
****


``ncm-authconfig``: NCM component to manage system authentication services.


***********
DESCRIPTION
***********


The \ *authconfig*\  component manages the system authentication methods
on RedHat systems using the ``authconfig`` command.  In addition, it can
set additional operational parameters for LDAP authentication by
modifying the ``/etc/ldap.conf`` (SL5), the ``/etc/nslcd.conf`` (SL6)
or ``/etc/sssd/sssd.conf`` (EL6/7) files directly.
It will also enable/disable NSCD support on the client.


*******
EXAMPLE
*******



.. code-block:: perl

     include "components/authconfig/config";
 
     prefix "/software/components/authconfig";
     "active" = true;
 
     "safemode" = false;
 
     "usemd5" = true;
     "useshadow" = true;
     "usecache" = true;
 
     prefix "/software/components/authconfig/method/files";
     "enable" = true;
 
     prefix "/software/components/authconfig/method/ldap";
     "enable" = false;
     "nssonly" = false;
     "conffile" = "/etc/ldap.conf";
     "servers" = list ("tbn06.nikhef.nl", "hooimijt.nikhef.nl");
     "basedn" = "dc=farmnet,dc=nikhef,dc=nl";
     "tls/enable" = true;
     "binddn" = "cn=proxyuser,dc=example,dc=com";
     "bindpw" = "secret";
     "rootbinddn" = "cn=manager,dc=example,dc=com";
     "port" = 389;
     "timeouts/idle" = 3600;
     "timeouts/bind" = 30;
     "timeouts/search" = 30;
     "pam_filter" = "|(gid=1012)(gid=1013)";
     "pam_login_attribute" = "uid";
     "pam_groupdn" = "cn=SystemAdministrators,ou=DirectoryGroups,dc=farmnet,dc=nikhef,dc=nl";
     "pam_member_attribute" = "uniquemember";
     "tls/peercheck" = "yes";
 
     "tls/cacertfile" = undef;
     "tls/cacertdir" = undef;
     "tls/ciphers" = undef;
 
     "nss_base_passwd" = "OU=Users,OU=Organic Units,DC=cern,DC=ch";
     "nss_base_group" = "OU=SLC,OU=Workgroups,DC=cern,DC=ch";
     "bind_policy" = "soft";
     "nss_map_objectclass/posixAccount" = "user";
     "nss_map_objectclass/shadowAccount" = "user";
     "nss_map_objectclass/posixGroup" = "group";
     "nss_map_attribute/uid" = "sAMAccountName";
     "nss_map_attribute/homeDirectory" = "unixHomeDirectory";
     "nss_map_attribute/uniqueMember" = "member";
     "pam_login_attribute" = "sAMAccountName";
     "ssl" = "start_tls";
 
     "pam_min_uid" = "0"; # NOT IMPLEMENTED #
     "pam_max_uid" = "0";# NOT IMPLEMENTED #
 
     prefix "/software/components/authconfig/method/nis";
     "enable" = false;
     "domain" = "nikhef.nl";
     "servers" = list ( "ajax.nikhef.nl" );
 
     prefix "/software/components/authconfig/method/krb5";
     "enable" = false;
     "kdcs" = list ( "kdc.nikhef.nl" );
     "adminserver" = list ( "krbadmin.nikhef.nl" );
     "realm" = "NIKHEF.NL";
 
     prefix "/software/components/authconfig/method/smb";
     "enable" = false;
     "workgroup" = "NIKHEF";
     "servers" = list ( "paling.nikhef.nl" );
 
     prefix "/software/components/authconfig/method/hesiod";
     "enable" = false;
     "lhs" = "lefthanded";
     "rhs" = "righthanded";


