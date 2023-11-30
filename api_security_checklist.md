# API Security Checklist

## Object level authorization

- Verify that implemented authorization reflects user policies and documentation.
- Verify that the API implementation is not relying client side authentication.
- Verify that the server is hardened using the best practices of the OS vendor and framework in use.
- Verify that the API implementation check validates authentication and authorization data if a stateless design is in place.
- Verify that the API is using a well-tested crypto library to generate random UUIDs.

## Broken authentication

- Document all possible methods for authentication to the API.
- Require password reset APIs and one-time links generating endpoints to validate authentication and authorization per request.
- Implements standardard authentication best practices (token generation, password storage, mfa).
- Stateful APIs should have short-lived session tokens.
- Implement rate-limiting, lockout policies, and evaluate for weak passwords on all authentication endpoints.

## Excessive data exposure

- The API should not trust client input, always validate.
- Ensure API responses contains only what the API consumers really need, the less verbose the better.
- The API specification should define all request and responses.
- Elimate verbose error responses are make sure that they are clearly defined.
- Verify that all responses that contain PII require authentication and authorization.

## Lack of resources and rate limiting

- Implement rate limiting.
- Define a limit for the payload body in the API request.
- Require all requests that interact with backend resources to be authenticated and authorized.

## Broken functional level authorization

- Deny all access as a default.
- Disable unneccesary endpoints.
- Verify rate limiting is present in the content of computing/container resources.
- Ensure roles are granted based on specific needs.
- Verify that authorization is implemented correctly.

## Mass assignment

- Do not allow the API to automatically bind incoming data and internal
objects.
- Define and document all parameters and payloads.
- Ensure runtime enforcement of the defined parameters and payloads.

## Security misconfiguration
- Verify that the APIs deployment is repeatable and that hardening and patching is part of the SDLC.
- Automate the API deployment system to minimize configuration flaws.
- Disable unnecessary features for every API.
- Verify that the API restricts administrative access.

## Injection

- Verify that the API is validating all input and authentication/authorization, even for internal use.
- Use available request and response body validation and deny any that do not match the defined schema.

## Improper asset management

- Document all infrastructure and API endpoints.
- Verify that the hosting platform limits access to anything that should not be public.
- Verify that the platform limits access to production data, and that there are separate production and non-production environments.
- Verify architecture implements strict authentication, authorization, redirects, CORS, etc.

## Insufficient Logging & Monitoring

- Log all requests, failed authentication atttempts, input validation failures, etc.
- Ensure that logs are formatted to be consumable by other tools.
- Verify that the hosting platform secures log storage.
- Verify that access to the hosting platform is restricted and documented.
- Require logs to be rotated off the hosting platform to a separate, centralized logging service as soon as possible.
