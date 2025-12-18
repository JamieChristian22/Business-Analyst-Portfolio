# UAT Scripts

## UAT-01: Joiner Provisioning (Birthright)
1. Trigger HR hire event for test user (jobCode=RCM_BILLER)
2. Verify identity attributes and birthright role assignment
3. Verify directory + target app entitlements provisioned
**Expected:** success + notification + evidence logs

## UAT-02: Access Request + Approvals
1. Request RCM_Supervisor for 30 days with justification
2. Approve as manager → approve as app owner
**Expected:** approvals logged + access provisioned

## UAT-03: Time-bound Access Expiry
1. Request elevated access with end date
2. Verify auto-expire triggers deprovisioning
**Expected:** access removed automatically

## UAT-04: Leaver Deprovisioning SLA
1. Trigger termination event
2. Verify directory disabled and critical access revoked within 1 hour
**Expected:** SLA met + report available

## UAT-05: Certification Campaign
1. Launch campaign for high-risk billing roles
2. Revoke one user’s elevated access
**Expected:** revocation fulfilled + exportable results

## UAT-06: SoD Conflict Prevention
1. User with PAYMENT_POST requests REFUND_APPROVE
2. Confirm conflict blocks fulfillment; route exception
**Expected:** Security + Compliance approvals required and time-bound
