# ToolEntry

## Example Usage

```typescript
import { ToolEntry } from "@gram/functions-sdk/models/components";

let value: ToolEntry = {
  id: "<id>",
  name: "<value>",
  toolUrn: "<value>",
  type: "externalmcp",
};
```

## Fields

| Field                                                                     | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `annotations`                                                             | [components.ToolAnnotations](../../models/components/tool-annotations.md) | :heavy_minus_sign:                                                        | Tool annotations providing behavioral hints about the tool                |
| `httpMethod`                                                              | *string*                                                                  | :heavy_minus_sign:                                                        | HTTP method for HTTP tools (GET, POST, PUT, PATCH, DELETE)                |
| `id`                                                                      | *string*                                                                  | :heavy_check_mark:                                                        | The ID of the tool                                                        |
| `name`                                                                    | *string*                                                                  | :heavy_check_mark:                                                        | The name of the tool                                                      |
| `toolUrn`                                                                 | *string*                                                                  | :heavy_check_mark:                                                        | The URN of the tool                                                       |
| `type`                                                                    | [components.ToolEntryType](../../models/components/tool-entry-type.md)    | :heavy_check_mark:                                                        | N/A                                                                       |