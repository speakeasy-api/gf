# ValidateKeyResult

## Example Usage

```typescript
import { ValidateKeyResult } from "@gram/functions-sdk/models/components";

let value: ValidateKeyResult = {
  organization: {
    id: "<id>",
    name: "<value>",
    slug: "<value>",
  },
  projects: [],
  scopes: [
    "<value 1>",
    "<value 2>",
    "<value 3>",
  ],
};
```

## Fields

| Field                                                                                      | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `organization`                                                                             | [components.ValidateKeyOrganization](../../models/components/validate-key-organization.md) | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `projects`                                                                                 | [components.ValidateKeyProject](../../models/components/validate-key-project.md)[]         | :heavy_check_mark:                                                                         | The projects accessible with this key                                                      |
| `scopes`                                                                                   | *string*[]                                                                                 | :heavy_check_mark:                                                                         | List of permission scopes for this key                                                     |