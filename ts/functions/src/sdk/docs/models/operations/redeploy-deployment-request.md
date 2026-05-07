# RedeployDeploymentRequest

## Example Usage

```typescript
import { RedeployDeploymentRequest } from "@gram/functions-sdk/models/operations";

let value: RedeployDeploymentRequest = {
  body: {
    deploymentId: "<id>",
  },
};
```

## Fields

| Field                                                                              | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `gramKey`                                                                          | *string*                                                                           | :heavy_minus_sign:                                                                 | API Key header                                                                     |
| `gramSession`                                                                      | *string*                                                                           | :heavy_minus_sign:                                                                 | Session header                                                                     |
| `gramProject`                                                                      | *string*                                                                           | :heavy_minus_sign:                                                                 | project header                                                                     |
| `body`                                                                             | [components.RedeployRequestBody](../../models/components/redeploy-request-body.md) | :heavy_check_mark:                                                                 | N/A                                                                                |