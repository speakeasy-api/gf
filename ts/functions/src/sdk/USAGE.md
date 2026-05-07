<!-- Start SDK Example Usage [usage] -->
```typescript
import { Gram } from "@gram/functions-sdk";
import { openAsBlob } from "node:fs";

const gram = new Gram();

async function run() {
  const result = await gram.assets.uploadFunctions({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject:
        process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    contentLength: 858625,
    body: await openAsBlob("example.file"),
  });

  console.log(result);
}

run();

```
<!-- End SDK Example Usage [usage] -->