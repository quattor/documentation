
################
CAF\::TextRender
################


****
NAME
****


CAF::TextRender - Class for rendering structured text


********
SYNOPSIS
********



.. code-block:: perl

     use CAF::TextRender;
 
     my $module = 'tiny';
     my $trd = CAF::TextRender->new($module, $contents, log => $self);
     print "$trd"; # stringification
 
     $module = "yaml";
     $trd = CAF::TextRender->new($module, $contents, log => $self);
     # return CAF::FileWriter instance (rendered text already added)
     my $fh = $trd->filewriter('/some/path');
     die "Problem rendering the text" if (!defined($fh));
     $fh->close();



***********
DESCRIPTION
***********


This class simplyfies the generation of structured text like config files.
(It is based on 14.8.0 ncm-metaconfig).

Private methods
===============



- ``_initialize``
 
 Initialize the process object. Arguments:
 
 
 - ``module``
  
  The rendering module to use: either one of the following reserved values
  
  
  - json
   
   JSON format (using ``JSON::XS``) (JSON true and false have to be resp. ``\1`` and c<\0>)
   
  
  
  - yaml
   
   YAML (using ``YAML::XS``) (YAML true and false, either resp. ``<$YAML_BOOL-``{yes}>> and
   ``$YAML_BOOL->{no}``; or the strings ``$YAML_BOOL_PREFIX."true"`` and
   ``$YAML_BOOL_PREFIX."false"`` (There are known problems with creating hashrefs using the
   ``$YAML_BOOL->{yes}`` value for true; Perl seems to mess up the structure when creating
   the hashrefs))
   
  
  
  - properties
   
   Java properties format (using ``Config::Properties``),
   
  
  
  - tiny
   
   .INI format (using ``Config::Tiny``)
   
  
  
  (Previously available module <general> was removed in 15.12.
  Component writers needing this functionality can use
  the \ **CCM::TextRender**\  subclass instead).
  
  Or, for any other value, ``Template::Toolkit`` is used, and the ``module`` then indicates
  the relative path of the template to use.
  
 
 
 - ``contents``
  
  ``contents`` is a hash reference holding the contents to pass to the rendering module.
  
 
 
 It takes some extra optional arguments:
 
 
 - ``log``, ``eol`` and ``usecache``
  
  Handled by ``_initialize_textopts`` from \ **CAF::ObjectText**\ 
  
 
 
 - ``includepath``
  
  The basedirectory for TT template files, and the INCLUDE_PATH
  for the Template instance. The ``includepath`` is either a string
  (i.e. ':'-separated list of paths), an arrayref (of multiple include paths)
  or undef (the default '/usr/share/templates/quattor' is used).
  
 
 
 - ``relpath``
  
  The relative path w.r.t. the includepath to look for TT template files.
  This relative path should not be part of the module name, however it
  is not the INCLUDE_PATH. (In particular, any TT ``INCLUDE`` statement has
  to use it as the relative basepath).
  If ``relpath`` is undefined, the default 'metaconfig' is used. If you do not
  have a subdirectory in the includepath, use an empty string.
  
 
 
 - ``ttoptions``
  
  A hash-reference ``ttoptions`` with Template Toolkit options,
  except for INCLUDE_PATH which is forced via ``includepath`` option.
  By default, STRICT (default 0) and RECURSION (default 1) are set.
  
 
 



