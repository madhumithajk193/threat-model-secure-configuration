# Threat Model and Secure Configuration

## Objective
Threat-model a small web application and create a prioritized hardening plan based on realistic assets and abuse cases.

## Application
This project models a fictional **Student Portal Web Application**.

### Users
- Student
- Faculty
- Administrator

### Main components
- Web browser/client
- Student Portal application server
- Database
- External email service
- External dependencies such as libraries/CDN/package repositories

### Key assets
- Student accounts
- Passwords
- Personal information
- Course information
- Assignment submissions
- Authentication sessions
- Database
- Email-service credentials

## Trust Boundaries
1. Internet/user browser -> application server
2. Application server -> database
3. Application server -> external email service

## Data Flows
- Browser <-> application over HTTPS
- Application <-> database
- Application <-> external email service over HTTPS
- Application -> external dependencies

## STRIDE Threats
1. **Spoofing:** stolen student credentials are used to impersonate a student.
2. **Tampering:** unauthorized modification of student or assignment data.
3. **Repudiation:** a user denies performing an important action such as submitting an assignment.
4. **Information Disclosure:** unauthorized access to private student information.
5. **Denial of Service:** excessive requests reduce application availability.
6. **Elevation of Privilege:** a normal student obtains administrator-level access.

## Risk Ranking
- R1 Elevation of Privilege — High likelihood / High impact
- R2 Spoofing — High likelihood / High impact
- R3 Information Disclosure — High likelihood / High impact
- R4 Tampering — Medium likelihood / Medium impact
- R5 Repudiation — Medium likelihood / Medium impact
- R6 Denial of Service — Low likelihood / Medium impact

## Prioritized Hardening
High-priority controls focus on RBAC and server-side authorization, authentication and session protection, HTTPS, least privilege, and preventing sensitive information disclosure.

Medium-priority controls include input validation, authorization of data changes, audit logging, rate limiting, request-size limits, and timeouts.

## Verification
Each major control has a verification step in `hardening/hardening-checklist.md`. Testing should remain within localhost or an isolated VM; do not scan or test external systems.

## Files
- `threat-model/threat-model-diagram.png` — threat-model diagram
- `risk-register/risk-register.xlsx` — risk register
- `hardening/hardening-checklist.md` — prioritized hardening checklist
