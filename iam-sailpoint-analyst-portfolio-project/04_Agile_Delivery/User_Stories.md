# User Stories (Sample Backlog)

## US-001: Auto-provision birthright access on hire
**Epic:** E-01 Identity Lifecycle  
**As a** new hire in RCM Ops, **I want** my standard accounts and birthright roles provisioned from HR data, **so that** I can start work on day 1.

**Acceptance Criteria**
- Hire record triggers identity creation and birthright assignment based on jobCode/department/location
- Directory + 2 target apps are provisioned successfully
- User notification includes access summary
- Logs include actor + timestamp

## US-002: Rapid deprovisioning on termination
**Epic:** E-01 Identity Lifecycle  
**As a** Security/IAM analyst, **I want** termination events to revoke high-risk access within SLA, **so that** PHI risk is minimized.

**Acceptance Criteria**
- Termination event disables directory account
- High-risk app access revoked within 1 hour SLA
- Failures create alert + retry queue entry
- Completion report available

## US-003: Self-service request for elevated role
**Epic:** E-02 Access Request Catalog  
**As a** RCM employee, **I want** to request elevated access via catalog, **so that** approvals are consistent and auditable.

**Acceptance Criteria**
- Justification + duration required
- Manager approval required
- App owner approval required for sensitive roles
- Access expires automatically at end date

## US-004: Quarterly access certification for Billing App high-risk roles
**Epic:** E-04 Access Certifications  
**As an** app owner, **I want** quarterly campaigns, **so that** least privilege is enforced.

**Acceptance Criteria**
- Campaign includes high-risk roles
- Reviewers can approve/revoke with comments
- Revocations trigger deprovisioning
- Exportable results for audit

## US-005: Block SoD conflicts on request
**Epic:** E-05 SoD & Risk Policies  
**As Compliance**, **I want** SoD conflicts prevented, **so that** fraud risk is reduced.

**Acceptance Criteria**
- Policy detects conflicts against existing access
- Exception requires Security + Compliance approval
- Exceptions are time-bound and reported
