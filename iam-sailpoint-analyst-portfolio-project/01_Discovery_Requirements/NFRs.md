# Non-Functional Requirements (NFRs)

| ID | Category | Requirement | Priority | Rationale |
|---|---|---|---|---|
| NFR-01 | Security | MFA required for admin and approver accounts | Must | Reduce takeover risk |
| NFR-02 | Security | Least privilege; prohibit shared admin accounts | Must | Accountability |
| NFR-03 | Availability | Workflows available 99.9% during business hours | Must | Ops continuity |
| NFR-04 | Audit/Logging | Log approvals, changes, and entitlement events | Must | Evidence |
| NFR-05 | Privacy | Mask sensitive attributes in logs where feasible | Must | HIPAA/GDPR |
| NFR-06 | Reliability | Retry failed provisioning with alerting and queue visibility | Must | Stability |
| NFR-07 | Maintainability | Document configs, mappings, and ownership | Must | Support |
