# `mkciud`

This module assembles user-data files for use with [`cloud-init`](https://cloud-init.io/).

More information on the format of user-data files can be found [here](https://cloudinit.readthedocs.io/en/latest/topics/format.html).


## Command-line usage

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
