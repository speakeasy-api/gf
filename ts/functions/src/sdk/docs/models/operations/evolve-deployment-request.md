# EvolveDeploymentRequest

## Example Usage

```typescript
import { EvolveDeploymentRequest } from "@gram/functions-sdk/models/operations";

let value: EvolveDeploymentRequest = {
  body: {
    nonBlocking: false,
    upsertExternalMcps: [
      {
        name: "My Slack Integration",
        registryServerSpecifier: "slack",
        selectedRemotes: [
          "https://mcp.example.com/sse",
        ],
        slug: "<value>",
      },
    ],
  },
};
```

## Fields

| Field                                                           | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `gramKey`                                                       | *string*                                                        | :heavy_minus_sign:                                              | API Key header                                                  |
| `gramSession`                                                   | *string*                                                        | :heavy_minus_sign:                                              | Session header                                                  |
| `gramProject`                                                   | *string*                                                        | :heavy_minus_sign:                                              | project header                                                  |
| `body`                                                          | [components.EvolveForm](../../models/components/evolve-form.md) | :heavy_check_mark:                                              | N/A                                                             |