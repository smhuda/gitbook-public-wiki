---
description: >-
  This security checklist consists of security countermeasures when designing,
  testing, and releasing your API.
---

# Security Checklist

## Authentication

*  Avoid using `Basic Auth` header and use standard authentication instead, for example, [JWT](https://jwt.io/), [OAuth](https://oauth.net/) or similar alternative authentication mechanisms
* Avoid creation of your own 'Authentication', 'Encryption', 'Password Generation' or 'Storage' mechanisms and use strong and robust standards already in place
* Implement the use of `Max Retry` and jail features in on all login functionality
* Ensure to encrypt all sensitive data

## JSON Web Tokens \(JWT\)

* Use a random and complicated`JWT Secret`to ensure the token cannot be brute-forced
* Don't extract the algorithm from the header. Force the algorithm in the backend `HS256` or `RS256`
* Ensure that the `TTL` and `RTTL` which refer to 'Time To Live', are as short as possible
* Don't store sensitive data in the JWT payload. These payloads can be decoded using resources like [JWT Debugger](https://jwt.io/#debugger-io)

## Open Authorization \(OAuth\)

* Always validate `redirect_uri` server-side to allow only whitelisted URLs
* Ensure that communication is exchanged for code and not tokens and do not allow responses in tokens for example, `response_type=token`
* Use `state` as the parameter with a random hash to prevent CSRF on the authentication process
* Define the default scope, and validate scope parameters for each application

## Access

* Throttle request by limiting them to avoid DDoS and brute-force attacks
* Use HTTPS on server-side to avoid MiTM attacks
* Use `HSTS` header with SSL to avoid SSL Strip attack
* For private APIs, only allow access from whitelisted IPs/hosts

## Input

* Use the proper HTTP method according to the operation, for example, use `GET`, requests for 'reading' data,  `POST` requests for 'creation' of data, `PUT` and `PATCH`request to 'update or replace' the data and `DELETE`, to 'remove' data
* Ensure to respond with `405 Method Not Allowed` if a requested method isn't appropriate for the requested resource
* Validate `content-type` on request Accept header for content negotiation to allow the supported format for example `application/xml`, `application/json` and respond with `406 Not Acceptable` response if not matched
* Validate `content-type` of posted data as you accept for example `application/x-www-form-urlencoded`, `multipart/form-data`, `application/json`, etc.
* Validate user input to avoid common vulnerabilities in reference with the OWASP Top Ten such as SQL Injection, Cross-Site Scripting \(XSS\), Remote Code Execution amongst a list of others
* Don't use any sensitive data such as credentials, security tokens or API keys in the URLs and only use an Authorization Header
* Use an API Gateway service to enable caching, Rate Limit policies \(e.g. `Quota`, `Spike Arrest`, or `Concurrent Rate Limit`\) and deploy APIs resources dynamically.

## Processing

* Check if all the endpoints are protected behind authentication to avoid broken authentication process
* Use of resource identifiers should be avoided. It is recommended to use `/web/purhcase` instead of `/web/0098/purchase`
* Don't auto-increment identifiers and instead use `UUID` instead
* If you are parsing XML files, make sure entity parsing is not enabled to avoid XXE attacks
* If you are parsing XML files, make sure entity expansion is not enabled to avoid XML bomb via exponential entity expansion attack
* Use a CDN for file uploads
* If you are dealing with a large amount of data, use Workers and Queues to process as much as possible in the background and return response quickly to avoid HTTP Blocking.
* Ensure to set the `DEBUG` mode to `OFF`

## Output

* Ensure that the `X-Content-Type-Options: nosniff` header is set
* Ensure that the `X-Frame-Options: deny` header is set
* Send the `Content-Security-Policy: default-src 'none'` header
* Ensure that the fingerprinting headers such as `X-Powered-By`, `Server`, `X-AspNet-Version`, etc are removed promptly before an application or service goes into production
* Force the use of `content-type` for your response. If you return `application/json`, then your `content-type` response is `application/json`
* Don't return sensitive data like 'Credentials' or 'Security Tokens'
* Return the proper status code according to the operation completed for example`200 OK`, `400 Bad Request`, `401 Unauthorized`, `405 Method Not Allowed`, etc.

## Continuous Integration \(CI\) and Continuous Delivery \(CD\)

* Audit your design and implementation with unit/integration tests coverage
* Use a code review process and disregard self-approval
* Ensure that all components of your services are statically scanned by AV software before pushing to production, including vendor libraries and other dependencies
* Design a rollback solution for deployments

