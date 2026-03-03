# Architecture (High Level)

SDG is composed of:
- **Web UI** (admin + user workflows)
- **Gateway API** (enforcement + orchestration)
- **Meta Database** (users, roles, grants, targets, templates, logs)
- **Target Databases** (MySQL/Postgres demo targets)
- **Audit + Query Run Logging**
- **Integrity Snapshots** (verify changes over time)

Trust boundaries:
- Untrusted user input never becomes raw SQL.
- Only approved templates execute; parameters are validated.
- Target endpoints are allowlisted to prevent SSRF / internal pivoting.
