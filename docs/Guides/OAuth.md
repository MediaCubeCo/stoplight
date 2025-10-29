---
tags: [Guides, OAuth Guide]
stoplight-id: xxf1peto7qas8
---

# OAuth 2.0 Authorization Server API

## Introduction

This document describes the authorization process using the `authorization_code` grant type in OAuth 2.0. This method is used to obtain an access token after the user successfully authorizes the application. Code samples can be found at Cookbook section. 

## `authorization_code` Grant Flow

### Steps in the Process

1. The **Application** redirects the user to the authorization server.
2. The **User** logs in and approves the request on the authorization server.
3. The **Authorization Server** redirects the user back to the client with an `code`.
4. The **Application** exchanges the `code` for an `access_token`.
5. The **Authorization Server** returns the tokens to the client.

### Sequence Diagram

```mermaid
sequenceDiagram
    participant User
    participant Application
    participant AuthServer

    User->>Application: Requests access
    Application->>AuthServer: Redirects to authorization page
    User->>AuthServer: Logs in and approves
    AuthServer->>Application: Redirects with code
    Application->>AuthServer: Requests tokens (code)
    AuthServer->>Application: Returns access_token and refresh_token
```

## `partner` Grant Flow

The `partner` grant type is used by trusted partner applications to obtain API tokens without requiring user interaction.

This flow is typically applied when the partner system is pre-authorized and acts on behalf of its users or internal integrations.

### Steps in the Process

1. The **Partner Application** sends a request `POST /oauth/tokens` to the authorization server endpoint.
2. The **Authorization Server** validates the credentials and permissions.
3. If the request is valid, the server issues an `access_token`.
4. The **Partner Application** uses the `access_token` to access protected API endpoints.

See the [CookBook](Cookbook.md) – Payments section for implementation examples.
