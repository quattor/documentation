
############################
NCM\::Component\::spma\::apt
############################


****
NAME
****


``NCM::Component::spma::apt`` - NCM SPMA backend for apt


********
SYNOPSIS
********


This document describes how to control the behaviour of the package manager itself.
For information on how to manage packages with Quattor, please check
`http://quattor.org/documentation/2013/04/05/package-management.html <http://quattor.org/documentation/2013/04/05/package-management.html>`_.


***********
DESCRIPTION
***********


This plugin implements an apt backend for ``ncm-spma``, the approach taken is to defer as much work as possible to apt.

A single SPMA run consists of the following steps:


- Setup source directory if required



- Remove sources that are not found in the profile



- Update source cache from upstream sources



- Upgrade already installed packages



- Install packages specified in the profile that are not installed



- Mark any packages installed but not in the profile as automatically installed



- Ask apt to remove all automatically installed packages that are not satisfying dependencies of other packages




*********
RESOURCES
*********


Only a very minimal schema is implemented.

Sources listed under ``/software/repositories`` will be configured,
URLs should be followed by the suite and sections required e.g. ``http://example.org/debian unstable main``

Packages listed under ``/software/packages`` will be installed, version and architecture locking (including multiarch) is fully implemented.

