# Assets

## Overview

Manages assets used by Gram projects.

### Available Operations

* [uploadFunctions](#uploadfunctions) - uploadFunctions assets
* [uploadOpenAPIv3](#uploadopenapiv3) - uploadOpenAPIv3 assets

## uploadFunctions

Upload functions to Gram.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="uploadFunctions" method="post" path="/rpc/assets.uploadFunctions" -->
```typescript
import { Gram } from "@gram/functions-sdk";
import { openAsBlob } from "node:fs";

const gram = new Gram();

async function run() {
  const result = await gram.assets.uploadFunctions({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    contentLength: 858625,
    body: await openAsBlob("example.file"),
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { assetsUploadFunctions } from "@gram/functions-sdk/funcs/assets-upload-functions.js";
import { openAsBlob } from "node:fs";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await assetsUploadFunctions(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    contentLength: 858625,
    body: await openAsBlob("example.file"),
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("assetsUploadFunctions failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UploadFunctionsRequest](../../models/operations/upload-functions-request.md)                                                                                       | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.UploadFunctionsSecurity](../../models/operations/upload-functions-security.md)                                                                                     | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.UploadFunctionsResult](../../models/components/upload-functions-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |

## uploadOpenAPIv3

Upload an OpenAPI v3 document to Gram.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="uploadOpenAPIv3Asset" method="post" path="/rpc/assets.uploadOpenAPIv3" -->
```typescript
import { Gram } from "@gram/functions-sdk";
import { openAsBlob } from "node:fs";

const gram = new Gram();

async function run() {
  const result = await gram.assets.uploadOpenAPIv3({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    contentLength: 513080,
    body: await openAsBlob("example.file"),
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { assetsUploadOpenAPIv3 } from "@gram/functions-sdk/funcs/assets-upload-open-ap-iv3.js";
import { openAsBlob } from "node:fs";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await assetsUploadOpenAPIv3(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    contentLength: 513080,
    body: await openAsBlob("example.file"),
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("assetsUploadOpenAPIv3 failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UploadOpenAPIv3AssetRequest](../../models/operations/upload-open-ap-iv3-asset-request.md)                                                                          | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.UploadOpenAPIv3AssetSecurity](../../models/operations/upload-open-ap-iv3-asset-security.md)                                                                        | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.UploadOpenAPIv3Result](../../models/components/upload-open-ap-iv3-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |