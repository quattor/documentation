
############################
NCM\::Component\::useraccess
############################


***********
DESCRIPTION
***********


The useraccess NCM component allows to manage the different ways an user
can get into a machine. Currently it configures Kerberos access, SSH
public keys access and specific services via ACLs.

Remember that the settings for a user means \ **the ways to log in as
that user**\ .


*************************
BASIC COMPONENT STRUCTURE
*************************


Besides the classic ``component_structure fields``, it provides two more
fields, named ``users`` and ``roles``. ``users`` will contain the
authorization information for each user, and ``roles`` will contain a
set of credentials for users to accept. Both ``users`` and ``roles``
have the same structure.

All the fields are optional, so you can have Kerberos authentication
but no public keys, or an user can be authorized to no ACL-controlled
service. And, to make it clear:

\ **The entries for user "foo" are the different ways people can log in
as user "foo".**\ 


* ``/software/components/useraccess/configSerial``
 
 This property is an arbitrary string representing a configuration
 serial number. It is not interpreted in any way by the component. Its
 role is only to trig a component run when its value changes. This is
 necessary when the change is in a file external to the configuration,
 referred by a URL.
 


* ``/software/components/useraccess/acl_services``
 
 List of services that will have ACLs associated to them.
 


* ``/software/components/useraccess/{users,roles}/<id>/kerberos4``
 
 It is a list of the users who can log in using Kerberos v4
 tickets. The contents of this list will be appropriately formatted and
 written into ``~/.klogin``.
 


* ``/software/components/useraccess/{users,roles}/<id>/kerberos5``
 
 It is a list of the users who can log using Kerberos v5 tickets. The
 contents of this list will be appropriately formatted and written into
 ``~/.k5login``.
 


* ``/software/components/useraccess/{users,roles}/<id>/ssh_keys_urls``
 
 It is a list containing the \ **absolute URLs**\  where the public keys
 granted to login as this user can be found. The URL can have any
 schema LWP::UserAgent supports, and it has been tested with http://,
 https:// and file:// . Local files are admitted, if wanted.
 


* ``/software/components/useraccess/{users,roles}/<id>/ssh_keys``
 
 It is a list containing the \ **exact lines**\  to be added to
 ``~/.ssh/authorized_keys``.
 
 The preferred way for adding authorized_keys is ssh_keys_urls.
 


* ``/software/components/useraccess/{users,roles}/<id>/acls``
 
 It is a list of the ACL-controlled services the user is allowed to log
 in. This only applies to PAM controlled services. SSH is not (not
 necessarily) controlled by PAM.
 
 \ **IMPORTANT NOTE:**\  this will add the user to the given ACL, but will
 \ **not**\  force the service to use ACLs at all. To do so, add the service
 to ``/software/components/useraccess/acl_services``.
 


* ``/software/components/useraccess/{users,roles}/<id>/roles``
 
 List of strings. It contains the list of roles the user belongs
 to. Roles can be nested.
 
 It is a compile-time error to add an user to a non-existing role.
 


* ``/software/components/useraccess/users/<id>/managed_credentials``
 
 List of authentication methods the component will configure (and thus,
 fully control) for the user. It is a list of strings, with possible
 values ``ssh_keys``, ``kerberos4`` and ``kerberos5``.
 
 It defaults to control all credentials, change it if you want to
 control something by some other means. For instance, CERN uses a
 different tool to controls SSH public key authentication on user
 ``oracle``.
 



*****************
KERBEROS SETTINGS
*****************


Both ``kerberos4`` and ``kerberos5`` share the same structure. It
contains the following fields:


* ``/software/components/useraccess/<id>/kerberosX/realm`` : mandatory
 
 Kerberos' realm for authentication (the part behind the @ in
 ``.klogin``).
 


* ``/software/components/useraccess/<id>/kerberosX/principal`` : mandatory
 
 Principal identity for the user in the Kerberos ticket server.
 


* ``/software/components/useraccess/<id>/kerberosX/instance`` : optional
 
 "Instance" identity for the user. This is a sub-identity.
 


* ``/software/components/useraccess/<id>/kerberosX/host`` : optional
 
 Host from which the ticket must come for this identity. It is
 currently ignored.
 



**********
ROLES, now
**********


As of now, a role is a group of users who will share the same
settings: they will all be listed in the same ACLs, they will allow
access to the same set of public SSH keys, and so on.

An user can be "plugged" into a role and thus, he will automatically
get all the appropriate settings:


.. code-block:: perl

  "/software/components/useraccess/roles/myrole" = nlist (
     "kerberos4", nlist (
         "realm", "UAM.ES",
         "principal", "me"
     )
  );
 
  "/software/components/useraccess/users/root/roles" = list ("myrole");


And now,  can login as root using Kerberos v4 tickets.

Also, roles can be nested. However, there are no checks for cyclic
inclusions. Cyclic nesting will produce infinite loops at runtime, and
may consume lots of disk space.


********
EXAMPLES
********


Kerberos
========


Let's say evil Mr Burns and his lackey, Smithers want to log into
Homer's account:


.. code-block:: perl

  "/software/components/useraccess/users/homer/kerberos4" = list (nlist (
         "realm", "SPRINGFIELD.COM",
         "principal", "mrburns"),
     nlist ("realm", "SPRINGFIELD.COM",
         "principal", "smithers",
         "instance", "lackey"));


And apply the same to Kerberos v5.


One role to control them all
============================


What do you think Sauron did?


.. code-block:: perl

  "/software/components/useraccess/roles/rings" = nlist (
     "ssh_keys", list ("http://mordor.org/sauron.key",
         "http://mordor.org/badguy.key")
     )
  );
 
  "/software/components/useraccess/users/three/roles" = list ("rings");
  "/software/components/useraccess/users/seven/roles" = list ("rings");
  "/software/components/useraccess/users/nine/roles" = list ("rings");



Back to Springfield
===================


We all know how evil Mr Burns is. So, let's say he wants full control
on the Simpson family. And Homer wants to spy women at home:


.. code-block:: perl

  "/software/components/useraccess/roles/badburns" = nlist (
     "kerberos4", list (nlist (
         "realm", "SPRINGFIELD.COM",
         "principal", "mrburns")),
     "kerberos5", list (nlist (
         "realm", "SPRINGFIELD.COM",
         "principal", "mrburns")
         )
  );
 
  "/software/components/useraccess/roles/badhomer" = nlist (
     "kerberos4", list (nlist (
         "realm", "SPRINGFIELD.COM",
         "principal", "homer",
         "instance", "another_silly_project")),
     "acls", list ("system-auth") # Woops! now Homer can't log-in!
     );
 
  "/software/components/useraccess/users/marge/roles" = list (
     "badburns", "badhomer"
  );
 
  "/software/components/useraccess/users/bart/roles" = list (
     "badburns",
  );
 
  "/software/components/useraccess/users/lisa/roles" = list (
     "badburns", "badhomer"
  );
 
  "/software/components/useraccess/users/maggie/roles" = list (
     "badburns",
  );


Now, Mr Burns can log in as Homer, Marge, Bart, Lisa or Maggie using
Kerberos 4 and 5 tickets. And Marge and Lisa allow Homer to sneak
in. But, in the same way, an ACL for system-auth is created. And only
Marge and Lisa are on that ACL. Now, not Maggie, nor Bart nor Homer
can even log in (on PAM-controlled services).


Nesting roles
=============


As simple as we'd expect:


.. code-block:: perl

  "/software/components/useraccess/roles/superrole/roles" = list (
     "rolea", "roleb", "rolec"
  );


Remember that all roles (rolea, roleb and rolec) must exist at
validation time!



*********************
LOCKING USER ACCOUNTS
*********************


When you lock user accounts, it may not be enough to just lock them
with ``passwd -l``. Depending on how you configured SSH, a locked user
may still be able to log-in with his public key.

