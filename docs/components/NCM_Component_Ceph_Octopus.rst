
################################
NCM\::Component\::Ceph\::Octopus
################################


****
NAME
****


ncm-ceph: Configuration module for CEPH


***********
DESCRIPTION
***********


Configuration module for CEPH
This is the module for Ceph versions > 15.2.0 and schema version v2 with orchestrator


********************
IMPLEMENTED FEATURES
********************


Features that are implemented at this moment:


* Generating orchestrator yaml files and management of existing cluster (bootstrap not implemented)



* Configuration file generation



* All daemons should already be adopted for cephadm, and ceph orchestrator should be configured.         This is either part of the adoption process https://docs.ceph.com/en/latest/cephadm/adoption/
        or by bootstraping a new cluster (see initial creation)




****************
INITIAL CREATION
****************


- The schema details are annotated in the schema file.

- Example pan files are included in the examples folder and also in the test folders.

To set up the initial cluster, some steps should be taken:


1. The mgr(s) should have passwordless ssh access to all the hosts of the cluster         e.g. by distributing the public key(s) of the ceph-deploy host(s) over the cluster hosts
            (As described in the cephadm documentation:
                        https://docs.ceph.com/en/latest/cephadm/install/#add-hosts-to-the-cluster)



- 2. Run the bootstrap command:         See https://docs.ceph.com/en/latest/cephadm/install/#bootstrap-a-new-cluster



- 3. You'll need the generated pubkey and admin keyring to distribute over cluster



- 4. Run the component to start the configuration of the new cluster




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


The component is tested with Ceph version 15.2.8
