
### NAME

`NCM::Component::OpenNebula::Image` adds `OpenNebula` `VM` images
support to `NCM::Component::OpenNebula`.

#### Public methods

- get\_images

    Gets the image template from `TT` file
    and gathers the image names (`<fqdn`\_<vdx>>)
    and datastore names to store the new images.

- remove\_or\_create\_vm\_images

    Creates new `VM` images and it detects if the image is
    already available or not.
    Also it removes images if the remove flag is set.

- create\_vm\_images

    Creates new `VM` images.

- remove\_vm\_images

    Removes `VM` images.
    Updates `$ref_rimages` to track the removed images.

- check\_vm\_images\_list

    Checks the difference between two image lists
    to detect if the images were correctly created/removed.
