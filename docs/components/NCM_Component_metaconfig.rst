
############################
NCM\::Component\::metaconfig
############################


****
NAME
****


ncm-metaconfig: Configure services whose config format can be
rendered via ``EDG::WP4::CCM::TextRender``.


*********************
CONFIGURATION MODULES
*********************


The following formats can be rendered via ``EDG::WP4::CCM::TextRender``:


* general
 
 Uses Perl's `Config::General <http://search.cpan.org/search?query=Config%3a%3aGeneral&mode=module>`_. This leads to configuration files
 similar to this one:
 
 
 .. code-block:: perl
 
      <nlist>
        <another nlist>
          scalar value
          another scalar value
        </another nlist>
      </nlist>
      list_element 0
      list_element 1
      list_element 2
 
 


* tiny
 
 Uses Perl's `Config::Tiny <http://search.cpan.org/search?query=Config%3a%3aTiny&mode=module>`_, typically for ``key = value`` files or
 INI-like files with sections separated by ``[section]`` headers.
 


* yaml
 
 Uses Perl's `YAML::XS <http://search.cpan.org/search?query=YAML%3a%3aXS&mode=module>`_ for rendering YAML configuration files.
 


* json
 
 Uses `JSON::XS <http://search.cpan.org/search?query=JSON%3a%3aXS&mode=module>`_ for rendering JSON configuration files.
 


* properties
 
 Uses `Config::Properties <http://search.cpan.org/search?query=Config%3a%3aProperties&mode=module>`_ for rendering Java-style configuration
 files.
 


* Any other string
 
 Uses `Template::Toolkit <http://search.cpan.org/search?query=Template%3a%3aToolkit&mode=module>`_ for rendering configuration files in formats
 supplied by the user.
 
 The name of the template is given by this field. It \ **must**\  be a path
 relative to ``metaconfig/``, and the component actively sanitizes this
 field.
 



********
EXAMPLES
********


Configuring `/etc/ccm.conf`
===========================


The well-known `/etc/ccm.conf` can be defined like this:

Define a valid structure for the file
-------------------------------------



.. code-block:: perl

     type ccm_conf_file = {
         "profile" : type_absoluteURI
         "debug" : long(0..5)
         "force" : boolean = false
         ...
     };
 
     bind "/software/components/metaconfig/services/{/etc/ccm.conf}/contents" = ccm_conf_file;



Fill in the contents
--------------------



.. code-block:: perl

     prefix "/software/components/metaconfig/services/{/etc/ccm.conf}"
 
     "contents/profile" = "http://www.google.com";
     "module" = "general";



And that's it
-------------


Now, just compile and deploy. You should get the same results as with
old good ncm-ccm.



Generating an INI-like file
===========================


We can generate simple INI-like files with the ``Config::Tiny`` module.

Example schema
--------------


Let's imagine the file has two sections with one key each:


.. code-block:: perl

     # This is the first section, labeled "s1"
     type section_1 = {
        "a" : long
     };
 
     # This is the second section, labeled "s2"
     type section_2 = {
        "b" : string
     };
 
     # This is the full file structure
     type my_ini_file = {
        "s1" : section_1
        "s2" : section_2
     };
 
     bind "/software/components/metaconfig/services/{/etc/foo.ini}/contents" = my_ini_file;



Describing the file
-------------------


We'll define the permissions, who renders it and which daemons are associated to it.


.. code-block:: perl

     prefix "/software/components/metaconfig/services/{/etc/foo.ini}";
 
     "mode" = 0600;
     "owner" = "root";
     "group" = "root";
     "module" = "tiny";
     "daemons/foo" = "restart";
     "daemons/bar" = "reload";


And we'll ensure the module that renders it is installed (Yum-based
syntax here):


.. code-block:: perl

     "/software/packages/{perl-Config-Tiny}" = nlist();



Describing the file's contents
------------------------------


And now, we only have to specify the contents:


.. code-block:: perl

     prefix "/software/components/metaconfig/services/{/etc/foo.ini}/contents";
     "s1/a" = 42;
     "s2/b" = "hitchicker";



And that's it
-------------


That's it!  When you deploy your configuration you should see your
`/etc/foo.ini` in the correct location.


