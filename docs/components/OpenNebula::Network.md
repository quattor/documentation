
### NAME

`NCM::Component::OpenNebula::Network` adds `OpenNebula` `VirtualNetwork` 
configuration support to `NCM::Component::opennebula`.

#### Public methods

- update\_vn\_ar

    Updates `VirtualNetwork` `ARs`.

- get\_vnetars

    Gets the network `ARs` (address range) from `TT` file
    and gathers `VNet` names and IP/MAC addresses.

- remove\_and\_create\_vn\_ars

    Removes/creates `ARs` (address range).

- detect\_duplicate\_ars

    Detects duplicate `VirtualNetwork` `ARs` with
    same IPs or MACs.
    Removes duplicated `ARs` (if `QUATTOR` flag is set to true).

- create\_vn\_ars

    Creates `VirtualNetwork` `AR` leases.

- remove\_vn\_ars

    Removes <VirtualNetwork> `AR` leases.

- remove\_vn\_ars

    Detects [Quattor](../Unittesting/Quattor.md) flag within `AR` template.
