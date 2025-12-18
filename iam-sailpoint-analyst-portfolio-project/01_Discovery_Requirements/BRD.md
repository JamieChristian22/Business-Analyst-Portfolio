# Business Requirements Document (BRD) — IAM Modernization (SailPoint)

**Version:** 1.0  
**Date:** 2025-12-18

## Executive Summary
Implement identity governance and lifecycle automation using SailPoint to streamline access provisioning, strengthen security controls, and ensure audit-ready compliance across healthcare revenue cycle operations.

## Current State (As‑Is)
- Onboarding: managers email or submit tickets; provisioning varies by app owner
- Movers: role changes do not reliably trigger access updates
- Offboarding: delayed access removal; dependent on ticket queues
- Access reviews: spreadsheets + reminders; inconsistent completion
- Audit: evidence gathered manually from multiple teams

## Future State (To‑Be)
- HR event triggers SailPoint workflows for Joiner/Mover/Leaver
- RBAC: standardized business roles mapped to entitlements
- Access requests via catalog with policy-driven routing + SLAs
- Quarterly certifications for high-risk apps and SoD roles
- Evidence pack export for audit requests

## Business Requirements (BR)
- **BR-01** Automate provisioning for core roles based on HR attributes
- **BR-02** Enforce manager/app owner approvals for elevated access and PHI-sensitive roles
- **BR-03** Ensure termination events revoke high-risk access within 1 hour
- **BR-04** Maintain a searchable access catalog with role descriptions and owners
- **BR-05** Support time-bound access with automatic expiration
- **BR-06** Run quarterly access certifications for designated apps/roles
- **BR-07** Provide auditable logs for access grants, revocations, and approvals
- **BR-08** Implement SoD policy to prevent conflicting entitlements
- **BR-09** Provide reporting for SLAs, requests, and certifications
- **BR-10** Provide training materials and a support runbook

## Acceptance Criteria (business)
- 10 priority roles onboard successfully through SailPoint JML workflow
- 3 apps integrated (directory + 2 business apps) with provisioning
- UAT sign-off from Ops, Security, and Service Desk
- First certification campaign completes >95% by due date
