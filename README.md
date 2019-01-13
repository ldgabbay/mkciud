# `mkciud`

This module assembles user-data files for use with [`cloud-init`](https://cloud-init.io/).

More information on the format of user-data files can be found [here](https://cloudinit.readthedocs.io/en/latest/topics/format.html).

This package provides a command-line utility and a module for Python 3.

Type autodetection is done by looking for a recognized specifier in the first line of the file, such as `#!/bin/bash` or `#cloud-config`.


## Command-Line

```text
mkciud [ [type-specifier:]filename ]+
```

```text
python -m mkciud [ [type-specifier:]filename ]+
```

```text
type-specifiers:
    (default), (empty string), auto           autodetect
    cb, cloud-boothook                        cloud-boothook
    cc, cloud-config                          cloud-config
    ca, cloud-config-archive                  cloud-config-archive
    ph, part-handler                          part-handler
    uj, upstart-job                           upstart-job
    io, include-once, x-include-once-url      x-include-once-url
    in, include, x-include-url                x-include-url
    sh, shellscript, x-shellscript            x-shellscript
```

Outputs user-data to stdout. This will be binary data, so redirect to a file.


## Module

```python
import mkciud

userdata = mkciud.UserData()
for message_body, message_subtype in message_bodies_and_subtypes:
	userdata.add(message_body, message_subtype)
userdata.export(sys.stdout.buffer)
```
