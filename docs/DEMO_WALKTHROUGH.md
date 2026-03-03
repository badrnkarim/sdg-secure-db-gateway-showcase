# Demo Walkthrough (2–3 minutes)

1. **Admin Panel** — control plane entrypoint  
   Evidence: `docs/assets/admin_panel.png`

2. **RBAC Permission Management** — grant Role→Target/Template and User→Role  
   Evidence: `docs/assets/permissions.png`

3. **Templates** — approved queries only (no raw SQL)  
   Evidence: `docs/assets/templates.png`

4. **Execute template successfully**  
   Evidence: `docs/assets/dashboard_query_success.png`

5. **Enforcement proofs**
   - Disallowed target blocked (allowlist / SSRF-safe validation)  
     Evidence: `docs/assets/target_endpoint_blocked.png`
   - Dangerous SQL blocked (DROP denied)  
     Evidence: `docs/assets/sql_blocked_drop.png`

6. **Integrity verification**
   - Match (verified) + mismatch (change detected)  
     Evidence: `docs/assets/integrity_match.png`, `docs/assets/integrity_mismatch.png`
