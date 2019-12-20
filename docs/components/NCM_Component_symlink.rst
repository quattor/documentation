
#########################
NCM\::Component\::symlink
#########################


****
NAME
****


symlink : symlink NCM component.


***********
DESCRIPTION
***********


Object to create/delete symbolic links. When creating symlinks, target existence
can be checked. And clobbering can be disabled. Also, target definition
can be simplified by the use of contextual variables and command outputs.


********
EXAMPLES
********



- Define global variable osdir so that it can be use to define symlink targets
 
 
 .. code-block:: perl
 
    "/software/components/symlink/context" = {
      append(nlist(
               "name",    "ostype",
               "value",   "@@uname@@",
      ));
    };
 
 


- Various symlink definition examples
 
 
 .. code-block:: perl
 
    "/software/components/symlink/links" = {
  
        # Define `/usr/bin/tcsh` only if `/bin/tcsh` exists
        append(nlist(
                "name",    "/usr/bin/tcsh",
                "target",   "/bin/tcsh",
                "exists",    true
        ));
  
        # Define `/atlas` with a target actual value including C<uname> command output
        append(nlist(
                "name",    "/atlas",
                "target",   "/atlas_prod/@@uname@@",
                "exist",    true
        ));
  
        # Define `/lhcb` with a target actual value including a contextual variable.
        # The contextual variable can be defined before or later in the configuration.
        append(nlist(
                "name",    "/lhcb",
                "target",   "/lhcb_prod/{ostype}",
                "exists",    true
        ));
  
        # Define `/usr/local` as a symlink only if the `/lal/prod/{ostype}` exists
        append(nlist(
                 "name",    "/usr/local",
                 "target",   "/lal_prod/{ostype}",
                 "exists",    true
        ));
  
        # Define symlink `/etc/alpine/conf`, replacing an existing
        # file by the symlink without renaming it
        append(nlist(
                 "name", "/etc/alpine/pine.conf",
                 "target", "/lal/gen/etc/pine.conf",
                 "replace",  nlist("all", "yes"),
        ));
  
        # Define symlink `/etc/pine.conf`, replacing an existing file or symlink
        # by the new symlink, after renaming it using extension .saved
        append(nlist(
                 "name", "/etc/pine.conf",
                 "target", "/lal/gen/etc/pine.conf",
                 "replace",  nlist("none", ".saved", "file", "yes", "link", "yes"),
        ));
  
        # Define `/htdocs` as a link only if `/htdocs` doesn't exist or already
        # exists as a symlink (actual target not checked)
        append(nlist(
            "name", "/htdocs",
            "target", HTTPD_HTDOCS_DIR,
            "replace",  nlist("all","no","link", "yes")
        ));
  
    # End of symlink definitions
    };
 
 


- Define options to enable replacement of empty directories and links, with empty directories renamed adding ``.saved`` to their name before defining the symlink.
 
 
 .. code-block:: perl
 
    "/software/components/symlink/options/replace/dirempty" = ".saved";
    "/software/components/symlink/options/replace/link" = "yes";
 
 


