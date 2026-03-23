---
name: security-audit
description: Runs a comprehensive security audit on the codebase. Checks for secrets, encryption, auth issues, OWASP compliance. Use before any release.
disable-model-invocation: true
context: fork
---

# Security Audit Skill

Comprehensive security audit for application code.

## Audit Steps

### 1. Secret Scanning
- Search for hardcoded API keys, tokens, passwords
- Check `.env` files are in `.gitignore`
- Verify no secrets in git history
- Patterns: `api_key`, `secret`, `password`, `token`, `Bearer`, `sk-`, `pk_`

### 2. Encryption Verification
- Sensitive data encrypted at rest
- Encryption keys stored in secure platform keystore
- No plaintext sensitive data in logs, temp files, or cache
- Key management follows security best practices

### 3. Authentication Review
- Auth tokens stored securely
- Session refresh logic handles edge cases
- MFA properly configured (if applicable)
- No auth bypass paths in route guards

### 4. OWASP Check

#### Web (Top 10)
- A01: Broken Access Control
- A02: Cryptographic Failures
- A03: Injection
- A04: Insecure Design
- A05: Security Misconfiguration
- A06: Vulnerable Components
- A07: Authentication Failures
- A08: Data Integrity Failures
- A09: Logging/Monitoring Failures
- A10: SSRF

#### Mobile (Top 10)
- M1: Improper Credential Usage
- M2: Inadequate Supply Chain Security
- M3: Insecure Authentication/Authorization
- M4: Insufficient Input/Output Validation
- M5: Insecure Communication
- M6: Inadequate Privacy Controls
- M7: Insufficient Binary Protections
- M8: Security Misconfiguration
- M9: Insecure Data Storage
- M10: Insufficient Cryptography

### 5. Dependency Audit
- Check for known vulnerabilities in dependencies
- Verify all packages are from trusted publishers
- Review dependency update status

### 6. Platform Security
- Check platform manifests/configs for misconfigurations
- Verify unnecessary permissions are not requested
- Ensure obfuscation/minification for release builds
