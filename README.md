# schemas
Data schemas provided by Dock


# Base Dock schema

In order to provide unified and verifiable protocol operations it is
important to have a few "metadata fields" included in each package.

This is achieved by adding the
[dock base](https://getdock.github.io/schemas/dock.json) schema into
your root schema using the `allOf` keyword. This will include all fields from the Dock schema:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "allOf": [
    {
      "$ref": "https://getdock.github.io/schemas/dock.json"
    }
  ],
  "$data": ["..."]
}
```

Where:

- `$schema`: denotes what schema was used to build this particular package. It is required to let the recipient know what's inside the package.
- `$originAddress`: address of the participant that created the data contained in this data package.
- `$recipientAddress`: address of the designated recipient.
- `$createdAt`: time value that denotes when the original data was created.
- `$data`: key that stores the package payload.