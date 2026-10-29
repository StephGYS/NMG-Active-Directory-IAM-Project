# Role-Based Access Control (RBAC) Structure

## Project: Northstar Medical Group

### 1. Purpose

This document describes the Active Directory organizational structure and role-based access control approach implemented in the Northstar Medical Group lab.

The objective is to organize employee identities by department, simplify account administration, and support the principle of least privilege.

### 2. Organizational Unit Structure

| Department | Organizational Unit | Security Group |
|---|---|---|
| Finance | Finance OU | Finance-Users |
| Human Resources | HR OU | HR-Users |
| Information Technology | IT OU | IT-Users |
| Operations | Operations OU | Operations-Users |

### 3. RBAC Design

Security groups are used to organize users according to their departmental responsibilities.

- **Finance-Users:** Intended for employees who require access to authorized financial resources.
- **HR-Users:** Intended for employees responsible for human resources activities.
- **IT-Users:** Intended for IT staff who require access appropriate to their technical responsibilities.
- **Operations-Users:** Intended for employees responsible for operational activities.

Group membership alone does not automatically grant access to resources. Appropriate permissions must also be configured.

### 4. Principle of Least Privilege

Employees should receive only the permissions necessary to perform their assigned duties.

For example, an HR employee should not automatically receive access to Finance documents unless a legitimate business requirement exists and the access is explicitly authorized.

### 5. Day 4 — Jane Cooper Incident

During Day 4, an account configuration issue involving Jane Cooper was investigated.

The investigation identified incorrect organizational placement and group membership.

Corrective actions included:

- Moving Jane Cooper's account into the appropriate HR organizational unit.
- Updating her departmental security group membership.
- Reviewing the corrected account configuration in Active Directory.

**Verification limitation:** Access to an HR shared folder was not tested because that shared resource had not been created. Therefore, successful HR file access cannot yet be confirmed.

### 6. Security Benefits

This design supports:

- Centralized identity administration.
- Consistent departmental group assignments.
- Reduced risk of unnecessary access.
- Easier onboarding and offboarding.
- Improved accountability and troubleshooting.

### 7. Conclusion

The Northstar Medical Group lab demonstrates how Active Directory organizational units and security groups can support structured identity and access management.

Future validation should include configuring resource permissions and testing effective access with departmental user accounts.
