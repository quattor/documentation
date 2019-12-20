
#################################
NCM\::Component\::Ceph\::Luminous
#################################


****
NAME
****


ncm-ceph: Configuration module for CEPH


***********
DESCRIPTION
***********


Configuration module for CEPH
This is the module for Ceph versions > 12.2.2 and schema version v2


********************
IMPLEMENTED FEATURES
********************


Features that are implemented at this moment:


* Creating cluster (manual step involved)



* Set admin hosts for monitors



* Configuration file generation



* Checking/adding Monitors and Managers on deployhost



* Checking/adding OSDs per OSD host



* Checking/adding MDSs on deployhost



* Wildcard support in version numbers



The implementation has some safety features. Therefore:


* The config of MON, OSD and MDSs are first checked. If no errors were found, the actual changes will be deployed.



* No removals of MONs, OSDs or MDSs are done. No zapping of disks is implemented.



* When something is not right and returns an error, the whole component exits.



* You can set the version of ceph and ceph-deploy in the Quattor scheme. The component will then only run if the versions of ceph and ceph-deploy match with those versions.




****************
INITIAL CREATION
****************


- The schema details are annotated in the schema file.

- Example pan files are included in the examples folder and also in the test folders.

To set up the initial cluster, some steps should be taken:


1. First create a ceph user on all the hosts, using ceph-user.pan



- 2. The deployhost(s) should have passwordless ssh access to all the hosts of the cluster         e.g. by distributing the public key(s) of the ceph-deploy host(s) over the cluster hosts
            (As described in the ceph-deploy documentation:
                        http://ceph.com/docs/master/start/quick-start-preflight/)



- 3. The user should be able to run commands with sudo without password included in sudo.pan



- 4. Run the component a first time.             It shall fail, but you should get the initial command for your cluster



- 5. Run this command



- 6. Run the component again to start the configuration of the new cluster



- 7. When the component now runs on OSD servers, it will deploy the local OSDs




*********
RESOURCES
*********


`/software/components/ceph`
===========================


The configuration information for the component.  Each field should
be described in this section.



************
DEPENDENCIES
************


The component is tested with Ceph version 12.2.2 and ceph-deploy version 1.5.39.
