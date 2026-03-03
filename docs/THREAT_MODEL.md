# Threat Model (SDG)

## Assets
- Target DB connectivity controls
- Templates + RBAC grants (authorization policy)
- Audit data (Activity Log, Query Run History)
- Integrity snapshot hashes

## Trust boundaries
UI → Gateway API → Meta DB / Target DBs

## Key threats & mitigations
- **Unauthorized access** → RBAC (deny-by-default), explicit grants, audit trail
- **SQL injection / destructive SQL** → template-only execution + SQL safety enforcement
- **SSRF / internal pivot via Targets** → allowlist validation (“endpoint not allowed”)
- **Privilege escalation** → controlled admin workflows + logging
- **Tampering** → integrity snapshots (match/mismatch verification)

## Hardening roadmap
- External KMS + key rotation
- Rate limiting for sensitive operations
- Detection signals for abnormal template usage
