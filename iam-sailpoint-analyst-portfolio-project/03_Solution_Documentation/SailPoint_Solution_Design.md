# Solution Design Summary — SailPoint IAM (Healthcare RCM)

## Architecture (logical)
- Source of truth: HRIS (worker status, dept, manager, job code, location)
- Identity governance: SailPoint (IdentityIQ/IdentityNow)
- Directory: Azure AD / Active Directory
- Target apps (examples): Billing/RCM platform, patient accounting, ticketing

## Role model (tiered)
Business roles (examples): RCM_Biller, RCM_Coder, RCM_AR_Rep, RCM_Supervisor, RCM_Refund_Specialist (SoD), IAM_Admin (restricted)

## Catalog rules
- Birthright roles auto-assigned on hire
- Elevated roles require manager + app owner approvals
- Elevated access defaults to 90-day expiration unless justified
- SoD checks executed before fulfillment

## Certifications
- Quarterly for high-risk apps/roles
- Monthly for privileged/admin roles
