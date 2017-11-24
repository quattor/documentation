
### NAME

`ncm-cron` -- NCM component to control cron entries for Linux and Solaris.

### DESCRIPTION

The _cron_ component manages files in the `/etc/cron.d` directory on Linux
and the `/var/spool/cron/crontabs` directory on Solaris.

#### Linux

Files managed by `ncm-cron` will have the `.ncm-cron.cron` suffix.  Other files in
the directory are not affected by this component. The name of each file will be
taken from the `name` attribute.

#### Solaris

Solaris uses an older version of cron that does not make use of a cron.d
directory for crontabs. `ncm-cron` **shares** the crontab with each user. To make
this work `ncm-cron` uses the concept of separate file **sections** within the
crontab.  Each **section** is identified by the use of the tags `NCM-CRON BEGIN:`
and `NCM-CRON END:`. Entries either side of these section identifiers are not
modified.

Solaris **does** have a `/etc/cron.d` directory, however it uses this directory
for control files such as `cron.allow` and `cron.deny`.

### EXAMPLE

    "/software/components/cron/entries" = list(
      dict(
        "name", "ls",
        "user", "root",
        "group", "root",
        "frequency", "*/2 * * * *",
        "command", "/bin/ls"),
      dict(
        "name", "hostname",
        "comment", "some interesting text",
        "frequency", "*/2 * * * *",
        "command", "/bin/hostname"),
        "env", dict("MAILTO", "admin@example.org"),
      dict(
        "name", "date",
        "comment", "runs the date sometime within a 3 hour period",
        "timing", dict(
            "minute", "0",
            "hour", "1",
            "smear", 180),
        "command", "/bin/date")
      );

On Linux this will create three files in `/etc/cron.d`:

    ls.ncm-cron.cron
    hostname.ncm-cron.cron
    date.ncm-cron.cron

On Solaris three extra entries will be added to the root crontab.

### Solaris

Editing the `NCM-CRON BEGIN:` and/or the `NCM-CRON END:` tag within a crontab will
cause unpredictable behaviour. Possible behavours are duplicate entries or
entries being removed altogether.

Editing BETWEEN the tags will cause the edits to be overwritten the next time
ncm-cron runs.
