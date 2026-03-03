# Security Control Matrix (SDG)

| Control | Risk mitigated | Evidence |
|---|---|---|
| RBAC grants (User→Role, Role→Target/Template) | Unauthorized access | `docs/assets/permissions.png` |
| Template-only SQL execution | Injection / unsafe execution | `docs/assets/templates.png` |
| SQL safety enforcement (block DROP, etc.) | Destructive operations | `docs/assets/sql_blocked_drop.png` |
| Target allowlist validation | SSRF / pivoting | `docs/assets/target_endpoint_blocked.png` |
| Controlled execution | Allowed actions run safely | `docs/assets/dashboard_query_success.png` |
| Integrity snapshots | Tamper/change visibility | `docs/assets/integrity_match.png`, `docs/assets/integrity_mismatch.png` |
