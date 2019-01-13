# `mkciud` -- make cloud-init user-data


## Usage

```text
mkciud [ [option] filename ]+
    -cb    cloud-boothook
    -cc    cloud-config
    -cca   cloud-config-archive
    -ph    part-handler
    -uj    upstart-job
    -io    x-include-once-url
    -i     x-include-url
    -sh    x-shellscript
```

Outputs user-data to stdout. This will be binary data, so redirect to a file.

This tool auto-detects the MIME subtype of each file based on the prefix.

This tool strips the prefix when unnecessary (e.g. `#cloud-config` is stripped, whereas `#!/bin/bash` is not.)
