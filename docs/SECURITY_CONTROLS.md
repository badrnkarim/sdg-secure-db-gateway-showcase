# Security Controls

## Authentication
- Password + OTP MFA for privileged actions / access.

## Authorization
- RBAC with explicit grants:
  - Role → Target
  - Role → Template
  - User → Role

## Execution Safety
- Template-only query execution (no raw SQL)
- Keyword + statement constraints to block destructive operations
- Parameter validation via schema

## Network Safety
- Target endpoint validation / allowlisting to mitigate SSRF-style abuse

## Auditability
- Activity Log: permission and admin actions
- Query Run History: status, timing, rows returned/affected, error capture

## Integrity
- Snapshots + verify to detect database changes
