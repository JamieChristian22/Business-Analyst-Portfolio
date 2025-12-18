# Role & Entitlement Mapping (Sample)

| Business Role | Description | Birthright? | Target System | Entitlements / Groups | Owner |
|---|---|---|---|---|---|
| RCM_Biller | Posts charges, works accounts | Yes | Billing App | BILLING_USER, AR_WORKQUEUE | Billing App Owner |
| RCM_Coder | Codes encounters | Yes | Coding App | CODER_USER, ICD10_TOOLS | Coding App Owner |
| RCM_AR_Rep | Follow-up and appeals | Yes | RCM Platform | AR_USER, APPEALS_QUEUE | RCM Platform Owner |
| RCM_Supervisor | Approves adjustments | No | Billing App | BILLING_SUPERVISOR | Revenue Ops Director |
| RCM_Refund_Specialist | Issues refunds | No (SoD) | Billing App | REFUND_INITIATE | Revenue Ops Director |
| IAM_Admin | SailPoint admin | No | SailPoint | ADMIN | IAM Manager |

## SoD Rules (examples)
- REFUND_INITIATE cannot be combined with ADJUSTMENT_APPROVE
- PAYMENT_POST cannot be combined with REFUND_APPROVE
- Exceptions require Security + Compliance approval and must be time-bound
