# schemas
Data schemas provided by Dock


# Base Dock schema

In order to provide unified and verifiable protocol operations it is
important to have few "metadata fields" included in each package.

This is achieved by adding
[dock base](https://github.com/getdock/schemas/base.json) schema into
your root schema using `allOf` keyword:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "allOf": [
    {
      "$ref": "https://github.com/getdock/schemas/dock.json"
    }
  ],
  "$data": ["..."]
}
```

This will include all fields from Dock schema:

- `$originAddress`: original address of the participant that created
  the data within this data package. This should remain unchanged during
  the repackaging process so that the final recipient would know who
  originally created this data (rather than the address of the user who
  repackaged the data)
- `$recipientAddress`: address of the designated recipient. This is the
  only field that is changed on every repackage. It is needed to ensure
  the recipient that the data was indeed designated for him.
- `$createdAt`: time value that denotes when original data was created.
  This should remain unchanged during the repackaging process to let the
  recipient see when original data was packaged.
- `$data`: key that stores the package payload.