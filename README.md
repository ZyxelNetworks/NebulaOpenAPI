# Zyxel Nebula API 

## Introduction

Zyxel Nebula is the solution to allow IT admins to control and manage Zyxel's Nebula-enabled access points, switches and gateways, all from one place with ease.

This document describes the APIs to automate the Nebula cloud management platform.

# Overview

- Zyxel Nebula API is RESTful and HTTPS protected.
- Zyxel Nebula API uses **API Key** instead of OAUTH2 to authenticate.

## RESTful API

The API endpoint is at
> https://api.nebula.zyxel.com/

Zyxel Nebula API uses JSON to exchange data thus HTTP `Content-Type` header must be `"application/json"`. Failed to provide the correct header will result HTTP `400` error.

For developing purpose please contact Zyxel for the `staging` API endpoint.

## API Key
Put the API key into the `X-ZyxelNebula-API-Key` header. If the API key fails to authenticate, HTTP `401` will be returned.

API key scope is per-Admin, and it shares the same permissions. Keep the API key safe for security reasons, or regenerate the API key when in doubt. The old key will be revoked if a new key is regenerated.

## Additional Response Header
In order to support debugging API usage, Zyxel Nebula API will add an additional response header `X-ZyxelNebula-API-RequestId` for tracing API. Developers should report this header to **Zyxel Nebula Developer Support** to get further information.

## Error
Zyxel Nebula API follows standard HTTP status code to indicate API error. For example, `200` indicates a successful API call while `404` means the resource is not found. `403` is returned if the API key has no permission to access the resources. In addition to the HTTP status code, a JSON response is always provided even if `200` is returned. The JSON example: 
```
{ "status": 401, "message": "Authentication required.", "code": 12345, "more_info": {} }
```
* `message` is human-readable sentence in English. It should **not** be presented to the end-user.
* `code` is an optional field. If it exists, it indicates additional error code, which can be used for extra error processing.
* `more_info` is also optional to provide the context of error `code` for developers to debug the API integration

## Variable Notation
Some APIs take variable to either process specified resources or change the settings differently. Notation like `{{variable}}` indicates the API can be called with a variable. When used in the response, variable can be used to identify resources that are dynamic.

## Common Resources
Because the API key is on behalf of the administrator, two basic resources are frequently referred in the API

| Resource  | Notation   | Description                |
|-----------|------------|----------------------------|
| Org ID    | {orgId}    | The unique ID for an Org   |
| Site ID   | {siteId}   | The unique ID for a Site   |
| Device ID | {devId}    | The unique ID for a Device |

Instead of using mutable Org/Site/Device Name, use these identifiers, which are opaque strings, to specify the resources.

## API Specification
Please refer [OpenAPI document](https://htmlpreview.github.io/?https://github.com/ZyxelNetworks/NebulaOpenAPI/blob/main/doc/openapi.html)
