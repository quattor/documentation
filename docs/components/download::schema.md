
### Types

 - `/software/download/component_download_file`
    - `/software/download/component_download_file/href`
        - Description: A URL (either absolute, or relative) that describes the source of the
      file. The URL can be specified as relative by ommitting the server
      name and/or the protocol, in which case the component defaults will be
      used. Local files can be used as source, such as
      file://localhost/etc/foo.txt or even file:///etc/foo.txt.
        - Optional
        - Type: string
    - `/software/download/component_download_file/post`
        - Description: Specify the command (no options allowed) to run
      whenever the file is updated.
      The filename is added as first and (only) argument.
      Note that if the update is
      optimised away by the download process (e.g. if the file is
      already up-to-date), the command will still be executed, so it
      is the responsibility of this command to determine what work
      needs to be done, if any.
        - Optional
        - Type: string
    - `/software/download/component_download_file/proxy`
        - Description: If false, then the proxy configuration will be ignored for
      this file. This has no effect when there are no proxy hosts defined.
        - Optional
        - Type: boolean
    - `/software/download/component_download_file/gssapi`
        - Description: If true, then curl/LWP will be invoked with GSSAPI Negotiate
      extension enabled, using the host keytab as the identity.
        - Optional
        - Type: boolean
    - `/software/download/component_download_file/perm`
        - Description: Sets the permissions of the file to the defined
      permissions (defined in octal, e.g. 0644).
        - Optional
        - Type: string
    - `/software/download/component_download_file/owner`
        - Description: Sets the ownership to given user (name or number).
        - Optional
        - Type: string
    - `/software/download/component_download_file/group`
        - Description: Sets the group ownership to the given group (name or number).
        - Optional
        - Type: string
    - `/software/download/component_download_file/min_age`
        - Description: Don't consider the remote file to be new until it is this number of minutes old
        - Optional
        - Type: long
    - `/software/download/component_download_file/cacert`
        - Optional
        - Type: string
    - `/software/download/component_download_file/capath`
        - Optional
        - Type: string
    - `/software/download/component_download_file/cert`
        - Optional
        - Type: string
    - `/software/download/component_download_file/key`
        - Optional
        - Type: string
    - `/software/download/component_download_file/timeout`
        - Description: seconds, overrides setting in component
        - Optional
        - Type: long
    - `/software/download/component_download_file/allow_older`
        - Description: allow older remote file
        - Optional
        - Type: boolean
 - `/software/download/download_component`
    - `/software/download/download_component/server`
        - Description: The default server hostname to use for any sources which
      do not specify the source.
        - Optional
        - Type: string
    - `/software/download/download_component/proto`
        - Description: The default protocol to use for any sources which do not
      specify the protocol.
        - Optional
        - Type: string
    - `/software/download/download_component/files`
        - Description: An dict of escaped filenames required for the destination file.
        - Optional
        - Type: component_download_file
    - `/software/download/download_component/proxyhosts`
        - Description: List of hostnames (and possibly with ':port' suffix).
      When specified, a reverse proxy configuration is assumed
      for all of the file sources. Whenever a file is downloaded, each of the
      proxy hosts will be used first before attempting the original source URL. The
      first proxy host to respond will be used for all subsequent download attempts.
        - Optional
        - Type: type_hostport
    - `/software/download/download_component/head_timeout`
        - Description: seconds, timeout for HEAD requests which checks for changes
        - Optional
        - Type: long
    - `/software/download/download_component/timeout`
        - Description: seconds, total timeout for fetch of file, can be overridden per file
        - Optional
        - Type: long
