# SDG One-Pager (Recruiter Summary)

**Secure Database Gateway (SDG)** is a security-first access layer between users and databases.

## Core Value
Instead of granting direct DB access, SDG becomes the single enforcement point for:
- Identity verification (MFA)
- Authorization (RBAC)
- Controlled execution (template-only SQL)
- Safety validation (SQL + SSRF controls)
- Full observability (audit trail + query run history)
- Integrity verification (snapshots)

## Why it matters
This design reduces credential sprawl, limits blast radius, and creates an auditable control plane for database operations.
