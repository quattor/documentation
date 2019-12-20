
##########################
NCM\::Component\::download
##########################


***********
DESCRIPTION
***********


Downloads files onto the local machine during the configuration,
and optionally post-processes the files.

The download is achieved by invoking ``curl``,
so any URLs acceptable to ``curl`` (and ``LWP::UserAgent``)
(including local ``file://`` URLs) are allowed.

A file is only downloaded if following conditions are met:


- The timestamp of the source can be retrieved



- The timestamp of the source is more recent than the current file (if such file exists); unless the ``allow_older`` attribute is set.



- The remote timestamp is not too recent.




********
EXAMPLES
********



.. code-block:: perl

     "/software/components/download" = dict(
         "server", "mydownloadserver.com",
         "proto",  "http",
     );
     prefix "/software/components/download/files";
     "{/etc/passwd}" = dict(
         "href", "https://secure.my.domain",
         "post", "/usr/local/mk_passwd",
     );
     "{/usr/local/foo.txt}" = dict(
         "href", "file:///etc/foo.txt",
         "owner", "john",
         "perm", "0400",
     );

