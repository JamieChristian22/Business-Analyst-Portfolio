# Test Strategy (IAM / SailPoint)

## Test types
- Configuration validation (rules, mappings, connector settings)
- Integration testing (HRIS feed, directory, target apps)
- Security testing (MFA, least privilege, admin restrictions)
- UAT (business validation of roles, requests, approvals, notifications)
- Regression (ensure changes don’t break existing roles/apps)

## Defect management
- Sev-1: blocks deprovisioning or creates PHI risk
- Sev-2: impacts workflow, workaround exists
- Sev-3: cosmetic/documentation
