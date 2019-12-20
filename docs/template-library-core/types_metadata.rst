################
types\::metadata
################

Types
-----

 - **structure_branch**
    - Description: Metadata about the source code management branch from which this profile was generated
    - *structure_branch/author*
        - Optional
        - Type: string
    - *structure_branch/name*
        - Required
        - Type: string
    - *structure_branch/type*
        - Required
        - Type: string
    - *structure_branch/commit-id*
        - Description: id/hash of (last) commit
        - Optional
        - Type: string
    - *structure_branch/timestamp*
        - Description: timestamp (in seconds since 1970), e.g. timestamp of last git commit
        - Optional
        - Type: long
        - Range: 0..
 - **structure_template**
    - Description: Metadata about the templates that generated this profile
    - *structure_template/branch*
        - Required
        - Type: structure_branch
 - **structure_metadata**
    - Description: Information about how the profile was generated. For example, the provenance of templates used as input to the compile, and which specific templates were selected for inclusion.
    - *structure_metadata/template*
        - Description: provenance of the template set
        - Required
        - Type: structure_template
    - *structure_metadata/features*
        - Description: list of templates from the features tree that were included
        - Optional
        - Type: string
