
### DESCRIPTION

ncm-freeipa provides support for FreeIPA configuration for

- server: add users, groups, services
- client: retrieve keytabs and certificates
- initialisation: get started n an already deployed host
- AII: add initialisation in kickstart and support removal

#### Server

On the server, create a keytab for the quattor-server user
    kinit admin

    uidadmin=`ipa user-show admin |grep UID: |sed "s/UID://;s/ //g;"`
    gidadmin=`ipa user-show admin |grep GID: |sed "s/GID://;s/ //g;"`
    # keep random password; it's already expired
    ipa user-add quattor-server --first=server --last=quattor --random --uid=$(($uidadmin+1)) --gidnumber=$(($gidadmin+1))
    kdestroy
    # use expired random password; and pick new random password (new password is not relevant)
    kinit quattor-server
    kdestroy

    kinit admin
    ipa role-add "Quattor server"
    for priv in "Host Administrators" "DNS Administrators" "Group Administrators" "Service Administrators" "User Administrators"; do
        ipa role-add-privilege "Quattor server" --privileges="$priv"
    done
    ipa role-add-member --users=quattor-server "Quattor server"
    # use -r option to retrieve existing keytab (e.g. from another ipa server)
    ipa-getkeytab -p quattor-server -k `/etc/quattor`-server.keytab -s ipaserver.example.com

Use these with ncm-freeipa on the server.

    prefix "/software/components/freeipa/principals/server";
    "principal" = "quattor-server";
    "keytab" = "/etc/quattor-server.keytab";

(Do not retrieve a keytab for the admin user;
it resets the admin password).

#### AII

The AII hooks act on behalf of the host it is going to setup, so
any of those principals cannot be used. Instead we use a fixed
AII principal and keytab.

First we need to add a user with appropriate privileges
    kinit admin

    uidadmin=`ipa user-show admin |grep UID: |sed "s/UID://;s/ //g;"`
    gidadmin=`ipa user-show admin |grep GID: |sed "s/GID://;s/ //g;"`
    # keep random password; it's already expired
    ipa user-add quattor-aii --first=aii --last=quattor --random --uid=$(($uidadmin+2)) --gidnumber=$(($gidadmin+2))
    kdestroy
    # use expired random password; and pick new random password (new password is not relevant)
    kinit quattor-aii
    kdestroy

    kinit admin
    ipa role-add "Quattor AII"
    ipa role-add-privilege "Quattor AII" --privileges="Host Administrators"
    ipa role-add-member --users=quattor-aii "Quattor AII"

On the AII host (assuming the host is already added to IPA)
    kinit admin
    # use -r option to retrieve existing keytab (e.g. from another AII server)
    ipa-getkeytab -p quattor-aii -k `/etc/quattor`-aii.keytab -s ipaserver.example.com
    kdestroy

(If you have granted the host principal the rights to retrieve the quattor-aii keytab,
you can add in the template of the AII host
    prefix "/software/components/freeipa/principals/aii";
    "principal" = "quattor-aii";
    "keytab" = "/etc/quattor-aii.keytab";
)

#### Missing

- role / privileges
- retrieve use keytabs
- AII principal/keytab via config file

### Methods

#### server

Configure server settings

#### server

Configure server settings
