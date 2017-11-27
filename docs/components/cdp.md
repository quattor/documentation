
### NAME

The _cdp_ component manages the configuration file
`/etc/cdp-listend.conf.`

### DESCRIPTION

The _cdp_ component manages the configuration file for the
cdp-listend daemon.

### EXAMPLES

    include 'components/cdp/config';
    prefix "/software/components/cdp";
    "fetch" = "/usr/sbin/ccm-fetch";
    "fetch_smear" = 30;
