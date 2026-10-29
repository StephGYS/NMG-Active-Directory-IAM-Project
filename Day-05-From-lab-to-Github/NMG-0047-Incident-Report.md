# Incident Report — NMG-0047

## Northstar Medical Group

**Incident Type:** Active Directory Account Misconfiguration  
**Affected User:** Jane Cooper (`jcooper`)  
**Department:** Human Resources  
**Status:** Account configuration corrected; resource access validation pending

## 1. Incident Summary

During Day 4 of the Northstar Medical Group Active Directory lab, a support ticket involving Jane Cooper was investigated.

The employee was experiencing an incorrect desktop environment following a departmental assignment change.

The investigation focused on her Active Directory organizational unit placement, security group membership, and the possible impact of Group Policy.

## 2. Investigation Findings

The investigation identified two account configuration issues:

- Jane Cooper's account was located in the Operations organizational unit rather than HR.
- Her departmental security group membership required correction to align with her HR responsibilities.

These findings indicated that her account configuration did not match her assigned department.

The OU misplacement could affect the application of OU-linked Group Policy Objects. However, the specific effective Group Policy settings were not independently verified.

## 3. Corrective Actions

The following corrective actions were performed:

1. Located Jane Cooper's account using Active Directory Users and Computers.
2. Reviewed her existing OU placement and group membership.
3. Moved her account into the HR organizational unit.
4. Updated her departmental security group membership to align with HR.
5. Reviewed the corrected OU placement and group membership in Active Directory.

## 4. Evidence Collected

Screenshots documenting the investigation and corrections are available in the Day 4 folder:

- `jane-original-ou.png`
- `jane-original-membership.png`
- `jane-corrected-ou-to-hr.png`
- `jane-corrected-membership-to-hr-users.png`
- `jane-hr-users-verification.png`

**Evidence location:** `Day-04-First-Support-Ticket/screenshots/`

## 5. Verification and Limitations

The screenshots document the account configuration before and after the corrective actions.

However, the following were not fully verified:

- Successful application of the intended HR Group Policy settings.
- Successful access to an HR shared folder.
- Effective NTFS and share permissions for HR resources.
- Confirmation that the original desktop issue was resolved after a new user sign-in.

An HR shared folder had not been created during this stage of the lab. Therefore, successful HR resource access cannot be claimed.

## 6. Root Cause Analysis

The identified account configuration problems were incorrect OU placement and inappropriate departmental group membership.

These misconfigurations could contribute to incorrect policy application and access-control issues.

However, the exact cause of the desktop behavior remains unconfirmed without effective Group Policy testing.

## 7. Security Lessons Learned

This investigation reinforced several important identity and access management concepts:

- Organizational units help organize accounts and determine the scope of OU-linked Group Policy.
- Security groups can simplify role-based permission assignments.
- The principle of least privilege requires removing unnecessary access.
- Group membership alone does not prove access to a resource.
- Corrective actions should be followed by technical verification before closing an incident.

## 8. Final Assessment

**Classification:** Identity and Access Management Misconfiguration

**Outcome:** OU placement and departmental group membership corrected.

**Remaining Work:** Validate Group Policy application, user desktop behavior, and effective resource access.

**Incident Status:** Partially resolved — verification pending.

## 9. Conclusion

Incident NMG-0047 provided practical experience investigating and correcting an Active Directory user-account misconfiguration.

The exercise demonstrated the importance of structured troubleshooting, appropriate security group assignments, least privilege, and evidence-based incident documentation.
