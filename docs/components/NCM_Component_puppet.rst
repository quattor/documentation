
########################
NCM\::Component\::puppet
########################


****
NAME
****


ncm-puppet: Component for running puppet standalone within quattor


*********
RESOURCES
*********



* ``/software/components/puppet/puppetconf``
 
 Defines the configuration for quattor. Each item is a section of the ``/etc/puppet/puppet.conf`` file.
 The section ``[main]`` is mandatory. Other sections may be added.
 


* ``/software/components/puppet/puppetconf/main``
 
 Each item is a parameter in the ``[main]`` section of the puppet.conf file. 
 The mandatory parameters are:
 
 
 * ``logdir`` :
  
  Puppet log dir. Defaults to ``/var/log/puppet``.
  
 
 
 * ``rundir`` : string
  
  Puppet run dir. Defaults to ``/var/log/puppet``.
  
 
 


* ``/software/components/puppet/hieraconf``
 
 Defines the configuration for hiera. Each item is a key definition in the ``/etc/puppet/hiera.yaml`` file. 
 The default is:
 
 
 .. code-block:: perl
 
      ---
      :backends:
      - yaml
      :hierarchy:
      - quattor
      :yaml:
            :datadir: `/etc/puppet/hieradata`
 
 


* ``/software/components/puppet/nodefiles``
 
 Named list of node specific manifests. The component will run ``puppet --apply `/etc/puppet/manifests`/<file>``
 for each item <file> of the nlist. The parameters of each item are:
 
 
 * ``contents`` : string
  
  content of the file:
  
  The default for "nodefiles" is one file ``quattor_default.pp`` with content ``"hiera_include('classes')"``.
  
 
 


* ``/software/components/puppet/hieradata``
 
 Data to be passed to the hiera config. The data will be written in 
 ``/etc/puppet/hieradata/quattor.yaml``. Note: the nlist keys will be unescaped by the component.
 


* ``/software/components/puppet/modules``
 
 Named list of modules to be downloaded from the puppetlab forge. Each module has the following parameters:
 
 
 * ``version`` ? string
  
  version of the module.
  
 
 


