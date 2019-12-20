ncm-ncd
-------

Front end for executing Quattor configuration modules.

Uses
~~~~

Running specific configuration modules

To run a well-defined list of configuration modules together with their pre and post-dependencies, do:

.. code-block:: bash

   ncm-ncd --configure <module1> [<module2> ...]

For running all configuration modules use the --all option:

.. code-block:: bash

    ncm-ncd --configure --all

For listing available components Use the --list option. It is incompatible with --configure.

.. code-block:: bash

    ncm-ncd --list

See also the full help with ncm-ncd --help.

Content
~~~~~~~

.. toctree::
    :caption: ncm-ncd
    :maxdepth: 1
    :glob:

    ncm-ncd/*
