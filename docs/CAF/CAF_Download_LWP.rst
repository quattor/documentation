
####################
CAF\::Download\::LWP
####################


****
NAME
****


``CAF::Download::LWP`` class to use ``LWP`` (and ``Net::HTTPS``).


***********
DESCRIPTION
***********


``CAF::Download::LWP`` prepares ``LWP`` (and ``Net::HTTPS``) and
provides interface to ``LWP::UserAgent``.

Remarks wrt SSL/TLS:


- If LWP is recent enough (v8.333, e.g. on EL6+), the choice of SSL module will be the system default (typically ``IO::Socket::SSL`` when available, ``Net::SSL`` otherwise).
 
 The usual environment variable will not be honoured
 (this module will typically be executed in a minimal environment anyway).
 
 When LWP is too old, ``Net::SSL`` will be forced (e.g. on EL5).
 


- If LWP is recent enough and ``IO::Socket::SSL`` is the default, hostname verification is forced.




*******
METHODS
*******



- ``_initialize``
 
 Initialize the object.
 
 Optional arguments:
 
 
 - ``log``
  
  A ``CAF::Reporter`` object to log to.
  
 
 


- _get_ua
 
 Prepare the environment and initialise ``LWP::UserAgent``.
 Best-effort to handle ssl setup, ``Net::SSL`` vs ``IO::Socket::SSL``
 and ``verify_hostname``.
 
 Example usage
 
 
 .. code-block:: perl
 
      ...
      my $ua = $self->_get_ua(%opts);
  
      local %ENV = %ENV;
      $self->update_env(\%ENV);
      ...
 
 
 Returns the ``LWP::UserAgent`` instance or undef.
 
 Options
 
 
 - cacert: the CA file
 
 
 
 - cadir: the CA path
 
 
 
 - cert: the client certificate filename
 
 
 
 - key: the client certificate private key filename
 
 
 
 - ccache: the kerberos credential cache
 
 
 
 - timeout: set timeout
 
 
 


- _do_ua
 
 Initialise ``LWP::UserAgent`` using ``_get_ua`` method
 and run ``method`` with arrayref ``args``.
 
 All named options are passed to ``_get_ua``.
 

