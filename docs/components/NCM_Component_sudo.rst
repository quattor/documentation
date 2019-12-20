
######################
NCM\::Component\::sudo
######################


***********
DESCRIPTION
***********


The \ *sudo*\  component manages the sudo configuracion, I.E: edits
``/etc/sudoers``. It doesn't provide as strict and nice syntax and
semantic correction as visudo(8) does, but it tries to warn on most
common users' mistakes.


********
EXAMPLES
********


Try the following settings:
  prefix "/software/components/sudo";
  "general_options/options" = dict("insults", true);
  "user_aliases/FOO" = list("127.0.0.1");
  "privilege_lines" = list(dict(

      "user", "foo",
      "run_as", "ALL",
      "host", "ALL",
      "cmd", "ALL"
      ));

and see the resulting ``/etc/sudoers``.


********
WARNINGS
********


This component cannot perform such as exhaustive analysis as visudo
does. Be careful with what you specify on your profiles or you will
break sudo!!

