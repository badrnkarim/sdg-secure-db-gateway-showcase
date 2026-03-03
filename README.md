# Secure Database Gateway (SDG)

![CodeQL](https://github.com/badrnkarim/sdg-secure-db-gateway-showcase/actions/workflows/codeql.yml/badge.svg)
![License](https://img.shields.io/github/license/badrnkarim/sdg-secure-db-gateway-showcase)
![Last Commit](https://img.shields.io/github/last-commit/badrnkarim/sdg-secure-db-gateway-showcase)

**SDG** is a security-first gateway between users and databases. It enforces **MFA (OTP)**, **RBAC**, **template-only SQL execution**, **SQL safety controls**, **SSRF-safe target validation**, and **full auditability** (activity logs, query-run history, integrity snapshots).

> This repository is a **showcase** (documentation + UI evidence). It’s designed to be recruiter-friendly and audit-friendly.

---

## What SDG prevents (at a glance)
- Direct DB access sprawl and unmanaged credentials
- Raw SQL submission from users
- Dangerous statements (e.g., `DROP`) via safety enforcement
- Target endpoint abuse / internal pivoting (allowlist validation)
- Untracked admin actions (full audit trail)

---

## Architecture

```mermaid
flowchart LR
  U[User/Admin] --> UI[Web UI]
  UI --> API[SDG Gateway API]
  API --> META[(Meta DB: users/roles/grants/templates/targets/logs)]
  API --> T1[(Target DBs: MySQL/Postgres)]
  API --> LOGS[(Activity Log + Query Run History)]
  API --> INTEG[(Integrity Snapshots: hash & verify)]
```

More details: **docs/ARCHITECTURE.md**

---

## Key Security Controls

| Control | What it enforces | Evidence |
|---|---|---|
| MFA (OTP) | Stronger authentication for access | Project report + UI flows |
| RBAC | Explicit grants: Role→Target, Role→Template, User→Role | `docs/assets/permissions.png` |
| Template-only SQL | Users can’t submit raw SQL | `docs/assets/templates.png` |
| SQL safety | Blocks dangerous operations (e.g., DROP) | `docs/assets/sql_blocked_drop.png` |
| SSRF-safe targets | Allowlist endpoint validation | `docs/assets/target_endpoint_blocked.png` |
| Auditability | Activity Log + Query Run History | UI + report |
| Integrity snapshots | Detects changes over time | `docs/assets/integrity_match.png`, `integrity_mismatch.png` |

More details: **docs/SECURITY_CONTROLS.md**

---

## Screenshots (UI Evidence)

### Admin Panel
<p align="center">
  <img src="docs/assets/admin_panel.png" width="920" alt="Admin Panel">
</p>

<details>
<summary><b>Show more screenshots</b></summary>

**RBAC Permission Management**
<p align="center">
  <img src="docs/assets/permissions.png" width="920" alt="Permission Management">
</p>

**Templates (approved query templates)**
<p align="center">
  <img src="docs/assets/templates.png" width="920" alt="Templates">
</p>

**Controlled execution (template run success)**
<p align="center">
  <img src="docs/assets/dashboard_query_success.png" width="920" alt="Query Success">
</p>

**Integrity verification (match / mismatch)**
<p align="center">
  <img src="docs/assets/integrity_match.png" width="920" alt="Integrity Match">
</p>
<p align="center">
  <img src="docs/assets/integrity_mismatch.png" width="920" alt="Integrity Mismatch">
</p>

**Security enforcement proofs**
<p align="center">
  <img src="docs/assets/target_endpoint_blocked.png" width="920" alt="Target Endpoint Blocked">
</p>
<p align="center">
  <img src="docs/assets/sql_blocked_drop.png" width="920" alt="SQL Blocked">
</p>

</details>

Screenshot mapping: **docs/SCREENSHOTS.md**

---

## Documentation
- Full report (PDF): **docs/SDG_Project_Report.pdf**
- One-pager: **docs/ONE_PAGER.md**

---

## Ownership
**Owner / Maintainer:** Badr Karim  
Repo: https://github.com/badrnkarim/sdg-secure-db-gateway-showcase

See **AUTHORS.md** for contributors.

---

## License
MIT — see **LICENSE**.
