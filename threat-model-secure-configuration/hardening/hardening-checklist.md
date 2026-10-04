# Prioritized Hardening Checklist

## Scope
Fictional Student Portal Web Application. This is a defensive threat-model exercise. Testing, if performed, should remain on localhost or an isolated VM.

## High Priority

- [ ] Enforce role-based access control (RBAC).
- [ ] Perform server-side authorization checks on every protected endpoint/action.
- [ ] Use strong authentication and secure password handling.
- [ ] Protect authentication sessions with secure cookie/session settings.
- [ ] Use HTTPS for browser-to-application communication.
- [ ] Apply least-privilege access to student and administrator data.
- [ ] Prevent sensitive information from appearing in error messages or logs.

### Verification
- Confirm a normal student cannot access administrator functions.
- Confirm unauthenticated users cannot access protected resources.
- Confirm one student cannot retrieve another student's private records.
- Review logs and error responses for passwords, tokens, and unnecessary personal data.

## Medium Priority

- [ ] Validate and sanitize application input.
- [ ] Authorize all assignment/data modification operations.
- [ ] Keep audit logs for important actions.
- [ ] Add rate limiting to authentication and other sensitive endpoints.
- [ ] Set request-size and timeout limits.

### Verification
- Send invalid input to the local test application and confirm it is rejected safely.
- Confirm unauthorized update/delete requests are rejected.
- Confirm important actions produce timestamped audit records without secrets.
- Confirm repeated local requests are rate-limited.

## Risk Mapping

| Priority | Main Risk | Primary Control |
|---|---|---|
| High | Elevation of Privilege | RBAC + server-side authorization |
| High | Spoofing | Strong authentication + session protection |
| High | Information Disclosure | Least privilege + HTTPS + safe errors |
| Medium | Tampering | Input validation + authorization |
| Medium | Repudiation | Audit logging |
| Medium | Denial of Service | Rate limiting + limits/timeouts |

## Completion Evidence

Record the verification result for each control in the final README or a short evidence section. Redact secrets and personal data from screenshots and reports.
