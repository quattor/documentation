#################
types\::component
#################

Types
-----

 - **structure_component_dependency**
    - *structure_component_dependency/pre*
        - Optional
        - Type: string
    - *structure_component_dependency/post*
        - Optional
        - Type: string
 - **structure_component**
    - *structure_component/active*
        - Required
        - Type: boolean
        - Default value: true
    - *structure_component/dispatch*
        - Required
        - Type: boolean
        - Default value: true
    - *structure_component/version*
        - Optional
        - Type: string
    - *structure_component/register_change*
        - Optional
        - Type: element
    - *structure_component/dependencies*
        - Optional
        - Type: structure_component_dependency
    - *structure_component/ncm-module*
        - Optional
        - Type: string
