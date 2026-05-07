# Keys

## Overview

Managing system api keys.

### Available Operations

* [validate](#validate) - verifyKey keys

## validate

Verify an api key

### Example Usage

<!-- UsageSnippet language="typescript" operationID="validateAPIKey" method="get" path="/rpc/keys.verify" -->
```typescript
import { Gram } from "@gram/functions-sdk";

const gram = new Gram();

async function run() {
  const result = await gram.keys.validate({
    apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { keysValidate } from "@gram/functions-sdk/funcs/keys-validate.js";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await keysValidate(gram, {
    apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("keysValidate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ValidateAPIKeyRequest](../../models/operations/validate-api-key-request.md)                                                                                        | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.ValidateAPIKeySecurity](../../models/operations/validate-api-key-security.md)                                                                                      | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.ValidateKeyResult](../../models/components/validate-key-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |