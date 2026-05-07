# Deployments

## Overview

Manages deployments of tools from upstream sources.

### Available Operations

* [active](#active) - getActiveDeployment deployments
* [create](#create) - createDeployment deployments
* [evolveDeployment](#evolvedeployment) - evolve deployments
* [getById](#getbyid) - getDeployment deployments
* [latest](#latest) - getLatestDeployment deployments
* [redeployDeployment](#redeploydeployment) - redeploy deployments

## active

Get the active deployment for a project.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getActiveDeployment" method="get" path="/rpc/deployments.active" -->
```typescript
import { Gram } from "@gram/functions-sdk";

const gram = new Gram();

async function run() {
  const result = await gram.deployments.active({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { deploymentsActive } from "@gram/functions-sdk/funcs/deployments-active.js";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await deploymentsActive(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("deploymentsActive failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetActiveDeploymentRequest](../../models/operations/get-active-deployment-request.md)                                                                              | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.GetActiveDeploymentSecurity](../../models/operations/get-active-deployment-security.md)                                                                            | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.GetActiveDeploymentResult](../../models/components/get-active-deployment-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |

## create

Create a deployment to load tool definitions.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="createDeployment" method="post" path="/rpc/deployments.create" -->
```typescript
import { Gram } from "@gram/functions-sdk";

const gram = new Gram();

async function run() {
  const result = await gram.deployments.create({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    idempotencyKey: "01jqq0ajmb4qh9eppz48dejr2m",
    body: {
      externalId: "bc5f4a555e933e6861d12edba4c2d87ef6caf8e6",
      externalMcps: [
        {
          name: "My Slack Integration",
          registryServerSpecifier: "slack",
          selectedRemotes: [
            "https://mcp.example.com/sse",
          ],
          slug: "<value>",
        },
      ],
      githubPr: "1234",
      githubRepo: "speakeasyapi/gram",
      githubSha: "f33e693e9e12552043bc0ec5c37f1b8a9e076161",
      nonBlocking: false,
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { deploymentsCreate } from "@gram/functions-sdk/funcs/deployments-create.js";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await deploymentsCreate(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    idempotencyKey: "01jqq0ajmb4qh9eppz48dejr2m",
    body: {
      externalId: "bc5f4a555e933e6861d12edba4c2d87ef6caf8e6",
      externalMcps: [
        {
          name: "My Slack Integration",
          registryServerSpecifier: "slack",
          selectedRemotes: [
            "https://mcp.example.com/sse",
          ],
          slug: "<value>",
        },
      ],
      githubPr: "1234",
      githubRepo: "speakeasyapi/gram",
      githubSha: "f33e693e9e12552043bc0ec5c37f1b8a9e076161",
      nonBlocking: false,
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("deploymentsCreate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CreateDeploymentRequest](../../models/operations/create-deployment-request.md)                                                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CreateDeploymentSecurity](../../models/operations/create-deployment-security.md)                                                                                   | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.CreateDeploymentResult](../../models/components/create-deployment-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |

## evolveDeployment

Create a new deployment with additional or updated tool sources.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="evolveDeployment" method="post" path="/rpc/deployments.evolve" -->
```typescript
import { Gram } from "@gram/functions-sdk";

const gram = new Gram();

async function run() {
  const result = await gram.deployments.evolveDeployment({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
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
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { deploymentsEvolveDeployment } from "@gram/functions-sdk/funcs/deployments-evolve-deployment.js";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await deploymentsEvolveDeployment(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
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
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("deploymentsEvolveDeployment failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.EvolveDeploymentRequest](../../models/operations/evolve-deployment-request.md)                                                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.EvolveDeploymentSecurity](../../models/operations/evolve-deployment-security.md)                                                                                   | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.EvolveResult](../../models/components/evolve-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |

## getById

Get a deployment by its ID.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getDeployment" method="get" path="/rpc/deployments.get" -->
```typescript
import { Gram } from "@gram/functions-sdk";

const gram = new Gram();

async function run() {
  const result = await gram.deployments.getById({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    id: "<id>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { deploymentsGetById } from "@gram/functions-sdk/funcs/deployments-get-by-id.js";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await deploymentsGetById(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    id: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("deploymentsGetById failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetDeploymentRequest](../../models/operations/get-deployment-request.md)                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.GetDeploymentSecurity](../../models/operations/get-deployment-security.md)                                                                                         | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.GetDeploymentResult](../../models/components/get-deployment-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |

## latest

Get the latest deployment for a project.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getLatestDeployment" method="get" path="/rpc/deployments.latest" -->
```typescript
import { Gram } from "@gram/functions-sdk";

const gram = new Gram();

async function run() {
  const result = await gram.deployments.latest({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { deploymentsLatest } from "@gram/functions-sdk/funcs/deployments-latest.js";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await deploymentsLatest(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("deploymentsLatest failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetLatestDeploymentRequest](../../models/operations/get-latest-deployment-request.md)                                                                              | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.GetLatestDeploymentSecurity](../../models/operations/get-latest-deployment-security.md)                                                                            | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.GetLatestDeploymentResult](../../models/components/get-latest-deployment-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |

## redeployDeployment

Redeploys an existing deployment.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="redeployDeployment" method="post" path="/rpc/deployments.redeploy" -->
```typescript
import { Gram } from "@gram/functions-sdk";

const gram = new Gram();

async function run() {
  const result = await gram.deployments.redeployDeployment({
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    body: {
      deploymentId: "<id>",
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { GramCore } from "@gram/functions-sdk/core.js";
import { deploymentsRedeployDeployment } from "@gram/functions-sdk/funcs/deployments-redeploy-deployment.js";

// Use `GramCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const gram = new GramCore();

async function run() {
  const res = await deploymentsRedeployDeployment(gram, {
    option1: {
      apikeyHeaderGramKey: process.env["GRAM_APIKEY_HEADER_GRAM_KEY"] ?? "",
      projectSlugHeaderGramProject: process.env["GRAM_PROJECT_SLUG_HEADER_GRAM_PROJECT"] ?? "",
    },
  }, {
    body: {
      deploymentId: "<id>",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("deploymentsRedeployDeployment failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.RedeployDeploymentRequest](../../models/operations/redeploy-deployment-request.md)                                                                                 | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.RedeployDeploymentSecurity](../../models/operations/redeploy-deployment-security.md)                                                                               | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.RedeployResult](../../models/components/redeploy-result.md)\>**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| errors.ErrorT                     | 400, 401, 403, 404, 409, 415, 422 | application/json                  |
| errors.ErrorT                     | 500, 502                          | application/json                  |
| errors.GramDefaultError           | 4XX, 5XX                          | \*/\*                             |