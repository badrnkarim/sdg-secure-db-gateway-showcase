# Secure Database Gateway (SDG)

![CodeQL](https://github.com/badrnkarim/sdg-secure-db-gateway-showcase/actions/workflows/codeql.yml/badge.svg)
![License](https://img.shields.io/github/license/badrnkarim/sdg-secure-db-gateway-showcase)
![Last Commit](https://img.shields.io/github/last-commit/badrnkarim/sdg-secure-db-gateway-showcase)

**SDG** is a security-first access layer between users and databases. It enforces **MFA (OTP)**, **RBAC**, **template-only SQL execution**, **SQL safety controls**, **SSRF-safe target validation**, and **auditability** (logs + integrity snapshots).

This repository is a **US-grade showcase**, featuring complete documentation, architectural reports, and curated UI evidence to demonstrate security posture and best practices.

---

## Why this matters
Direct database access creates credential sprawl and weak auditability. SDG centralizes control into one rigid enforcement point:
- Authenticate strongly (**MFA**)
- Authorize explicitly (**RBAC grants**)
- Execute safely (**approved templates only**)
- Block abuse (**SQL safety + SSRF/allowlist**)
- Provide evidence (**logs + integrity verification**)

---

## Key security controls (evidence-based)

| Control | What it stops | Evidence |
|---|---|---|
| RBAC grants | Unauthorized access | `docs/assets/permissions.png` |
| Template-only SQL | Raw SQL / injection paths | `docs/assets/templates.png` |
| SQL safety enforcement | Destructive SQL (`DROP`, etc.) | `docs/assets/sql_blocked_drop.png` |
| Target allowlist validation | SSRF / internal pivoting | `docs/assets/target_endpoint_blocked.png` |
| Integrity snapshots | Silent DB changes | `docs/assets/integrity_match.png` / `docs/assets/integrity_mismatch.png` |

More details in `docs/CONTROL_MATRIX.md`.

---

## Architecture (high level)

```mermaid
flowchart LR
    %% Modern Styling
    classDef user fill:#2563eb,stroke:#1d4ed8,stroke-width:2px,color:#fff,rx:8px,ry:8px;
    classDef ui fill:#0ea5e9,stroke:#0284c7,stroke-width:2px,color:#fff,rx:8px,ry:8px;
    classDef api fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#fff,rx:8px,ry:8px;
    classDef db fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff,rx:8px,ry:8px;
    classDef security fill:#f43f5e,stroke:#e11d48,stroke-width:2px,color:#fff,rx:8px,ry:8px;
    classDef group fill:#f8fafc,stroke:#cbd5e1,stroke-width:2px,stroke-dasharray: 5 5,rx:10px,ry:10px,color:#334155;

    %% Nodes
    U[["👤 User / Admin"]]:::user
    
    subgraph Frontend ["Front-End Layer"]
        UI["🖥️ Web UI (Dashboard / Admin)"]:::ui
    end

    subgraph Core ["Gateway Enforcement Layer"]
        API["🛡️ API Gateway (AuthN & AuthZ)"]:::api
        INTEG["🔍 Integrity Engine (Hash & Verify)"]:::security
    end

    subgraph Storage ["Data Layer"]
        META[/"⚙️ Meta DB (Roles, Logs, Config)"/]:::db
        TDB[/"🗄️ Target DBs (MySQL / Postgres)"/]:::db
    end

    %% Flow
    U -- "HTTPS / MFA" --> Frontend
    UI -- "REST / Actions" --> API
    API -- "Audit & Enforce" --> META
    API -- "Execute Template" --> TDB
    INTEG -. "Scheduled Snapshots" .-> TDB
    API -. "Trigger Verification" .-> INTEG

    %% Grouping styling
    class Frontend,Core,Storage group;
```

## UI Evidence (Screenshots)

**Admin Panel**  
<img src="docs/assets/admin_panel.png" width="920" alt="Admin Panel">

<details>
<summary><b>Show full evidence set</b></summary>

<br>

**RBAC Permission Management**  
<img src="docs/assets/permissions.png" width="920" alt="Permissions">

**Approved Templates (no raw SQL)**  
<img src="docs/assets/templates.png" width="920" alt="Templates">

**Controlled execution (success)**  
<img src="docs/assets/dashboard_query_success.png" width="920" alt="Query success">

**Integrity verification (match / mismatch)**  
<img src="docs/assets/integrity_match.png" width="920" alt="Integrity match">  
<img src="docs/assets/integrity_mismatch.png" width="920" alt="Integrity mismatch">

**Enforcement proofs**  
<img src="docs/assets/target_endpoint_blocked.png" width="920" alt="Target blocked">  
<img src="docs/assets/sql_blocked_drop.png" width="920" alt="SQL blocked">

</details>

*Screenshot mapping index:* `docs/SCREENSHOTS.md`

---

## Documentation
- **Full report (PDF)**: `docs/SDG_Project_Report.pdf`
- **Demo walkthrough**: `docs/DEMO_WALKTHROUGH.md`
- **Threat model**: `docs/THREAT_MODEL.md`

---

## Ownership

- **Owner / Maintainer**: Badr Karim
- **GitHub**: [@badrnkarim](https://github.com/badrnkarim)

## License
MIT License — see [LICENSE](LICENSE) for details.
