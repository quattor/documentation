
################
Quattor\::Critic
################


****
NAME
****


Test::Quattor::Critic - Run Perl::Critic.


***********
DESCRIPTION
***********


This is a class to run Perl::Critic code with a whitelist of policies.

To get the policy names, use
    critic --cruel --verbose 8 path/to/perl/code


*******
METHODS
*******



- new
 
 
 - codedirs
  
  An arrayref of paths to look for perl code (uses ``Test::Pod::all_pod_files``).
  
  Default is ``target/lib/perl``.
  
 
 
 - exclude
  
  A regexp to remove policies from list of fatal policies.
  
 
 


- make_critic
 
 Create ``Perl::Critic`` instance and load policies
 


- check
 
 Given a list of ``Perl::Critic::Violations`` (e.g. as return value of
 ``critique`` method) and check which one should be reported on.
 


- test
 
 Run critic test on all files found with ``all_pod_files`` in all codedirs.
 


