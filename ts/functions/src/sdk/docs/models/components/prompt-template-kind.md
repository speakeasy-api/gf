# PromptTemplateKind

The kind of prompt the template is used for

## Example Usage

```typescript
import { PromptTemplateKind } from "@gram/functions-sdk/models/components";

let value: PromptTemplateKind = "higher_order_tool";

// Open enum: unrecognized values are captured as Unrecognized<string>
```

## Values

```typescript
"prompt" | "higher_order_tool" | Unrecognized<string>
```