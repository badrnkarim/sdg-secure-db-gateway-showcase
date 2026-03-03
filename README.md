# Secure Database Gateway (SDG)

Secure Database Gateway (SDG) is a **security-first access layer** between users and databases. It enforces **MFA (password + OTP)**, **RBAC authorization**, **template-only SQL execution**, **SQL safety controls**, **SSRF-safe target validation**, and **full auditability** (activity logs, query-run history, integrity snapshots).

## Key Security Controls
- **MFA**: password + OTP
- **RBAC**: explicit grants to targets/templates per role
- **Template-only SQL**: users cannot submit raw SQL
- **SQL safety**: blocks dangerous statements (e.g., DROP/ALTER/CREATE/TRUNCATE)
- **SSRF protection**: blocks non-allowed DB endpoints
- **Audit logging**: admin/user actions tracked
- **Query-run logging**: execution history + status + rows + errors
- **Integrity snapshots**: verify database changes over time

## Documentation
- Full report: `docs/SDG_Project_Report.pdf`

## UI Evidence (Screenshots)
Stored in `docs/assets/`.

![Admin Panel](docs/assets/admin_panel.png)
![Permissions](docs/assets/permissions.png)
![Templates](docs/assets/templates.png)
![Query Success](docs/assets/dashboard_query_success.png)
![Integrity Match](docs/assets/integrity_match.png)

### Security Enforcement Proof
![Target blocked](docs/assets/target_endpoint_blocked.png)
![SQL blocked](docs/assets/sql_blocked_drop.png)
![Integrity mismatch](docs/assets/integrity_mismatch.png)

## Links
- Homepage/Portfolio: https://github.com/badrnkarim/ISO27001-ISMS-GRC-Portfolio
