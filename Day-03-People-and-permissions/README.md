# Day 3 — Active Directory User Provisioning & Security Group Management

## 1. Project Overview

On Day 3 of my Active Directory cybersecurity home lab, I focused on **Identity and Access Management (IAM)** by creating employee accounts, organizing them into departmental Organizational Units (OUs), assigning security group memberships, and verifying the configuration using Windows PowerShell.

The lab simulates the IT environment of **Northstar Management Group (NMG)**, a fictional organization with four departments: Finance, Human Resources, Information Technology, and Operations.

The objective was to understand how organizations manage employee identities and use security groups as a foundation for access control.

## 2. Lab Environment

| Component | Configuration |
|---|---|
| Operating System | Windows Server 2019 |
| Domain | NMG.com |
| Directory Service | Active Directory Domain Services |
| Management Tool | Active Directory Users and Computers |
| Verification Tool | Windows PowerShell |
| Organizational Units | Finance, HR, IT, Operations |
| Total Employee Accounts | 15 |
| Departmental Security Groups | 4 |

## 3. Phase 1 — Employee Account Creation

I created 15 individual Active Directory user accounts across four departmental OUs.

Each employee received a unique username to support accountability, identity management, security monitoring, and incident investigations.

### 3.1 Finance Department

Created four Finance employees:

| Employee | Username | Job Title |
|---|---|---|
| David Chen | dchen | Finance Manager |
| Karen Mills | kmills | Finance Analyst |
| Robert Hayes | rhayes | Payroll Specialist |
| Lisa Park | lpark | Accounts Payable |

The accounts were created inside the Finance OU.

I also configured employee organization attributes, including job titles and departments.

**Evidence — Finance employee accounts**

![Finance employee accounts](images/day03-finance-users.png)

**Evidence — David Chen's organizational attributes**

![David Chen organizational attributes](images/day03-david-chen-attributes.png)

### 3.2 Human Resources Department

Created three HR employees:

| Employee | Username | Job Title |
|---|---|---|
| Sandra Torres | storres | HR Manager |
| James Whitfield | jwhitfield | HR Recruiter |
| Michelle Grant | mgrant | Benefits Coordinator |

These accounts were placed inside the HR OU.

**Evidence — HR employee accounts**

![HR employee accounts](images/day03-hr-users.png)

### 3.3 Information Technology Department

Created four IT employees:

| Employee | Username | Job Title |
|---|---|---|
| Marcus Johnson | mjohnson | IT Administrator |
| Priya Patel | ppatel | Security Analyst |
| Tyler Brooks | tbrooks | Help Desk Technician |
| Aisha Coleman | acoleman | Systems Engineer |

All accounts were created inside the IT OU.

Although these employees work in the same department, their job responsibilities differ. This demonstrates why administrative privileges should not automatically be shared among all IT personnel.

**Evidence — IT employee accounts**

![IT employee accounts](images/day03-it-users.png)

### 3.4 Operations Department

Created four Operations employees:

| Employee | Username | Job Title |
|---|---|---|
| Brian Foster | bfoster | Operations Manager |
| Jane Cooper | jcooper | Operations Coordinator |
| Carlos Rivera | crivera | Facilities Supervisor |
| Natalie Ross | nross | Scheduling Coordinator |

All four accounts were created inside the Operations OU.

Jane Cooper's account will also be used in future access-management exercises.

**Evidence — Operations employee accounts**

![Operations employee accounts](images/day03-operations-users.png)

## 4. Phase 2 — Security Group Membership

After creating the employee accounts, I assigned users to their appropriate departmental security groups.

The purpose of this phase was to practice managing identities collectively rather than configuring each employee's access individually.

### 4.1 Finance-Users

Added David Chen, Karen Mills, Robert Hayes, and Lisa Park to the Finance-Users security group.

I verified the membership through the group's **Members** tab.

**Evidence — Finance security group**

![Finance group membership](images/day03-finance-group-members.png)

### 4.2 HR-Users

Added Sandra Torres, James Whitfield, and Michelle Grant to HR-Users.

**Evidence — HR security group**

![HR group membership](images/day03-hr-group-members.png)

### 4.3 IT-Users

Added Marcus Johnson, Priya Patel, Tyler Brooks, and Aisha Coleman to IT-Users.

**Evidence — IT security group**

![IT group membership](images/day03-it-group-members.png)

### 4.4 Operations-Users

Added Brian Foster, Jane Cooper, Carlos Rivera, and Natalie Ross to Operations-Users.

**Evidence — Operations security group**

![Operations group membership](images/day03-operations-group-members.png)

### Important Security Observation

Being a member of a departmental security group does not automatically grant access to every resource belonging to that department.

Actual access depends on the permissions configured on the target resources and any other applicable access controls.

During this phase, I configured and verified group memberships. I did not yet configure or test departmental file permissions.

## 5. Phase 3 — PowerShell Verification

To independently verify the Active Directory configuration, I used Windows PowerShell to query the membership of each departmental security group.

Commands executed:

```powershell
Get-ADGroupMember -Identity "Finance-Users" |
Select-Object Name, SamAccountName

Get-ADGroupMember -Identity "HR-Users" |
Select-Object Name, SamAccountName

Get-ADGroupMember -Identity "IT-Users" |
Select-Object Name, SamAccountName

Get-ADGroupMember -Identity "Operations-Users" |
Select-Object Name, SamAccountName
```

### Verification Results

| Security Group | Members Verified |
|---|---|
| Finance-Users | 4 |
| HR-Users | 3 |
| IT-Users | 4 |
| Operations-Users | 4 |
| **Total** | **15** |

All four commands returned the expected employees and their corresponding usernames.

This confirmed that the 15 employee accounts had been assigned to the intended departmental security groups.

**Evidence — PowerShell verification**

![PowerShell group membership verification](images/day03-powershell-verification.png)

## 6. Cybersecurity Concepts Learned

### Identity and Access Management (IAM)

IAM involves managing digital identities and controlling their access to organizational resources.

Creating individual employee accounts provides a foundation for accountability, authentication, and authorization.

### Organizational Units vs. Security Groups

An Organizational Unit is used to organize Active Directory objects and support administrative delegation and Group Policy.

A security group is used to collect identities so permissions can be assigned and managed more efficiently.

Placing an employee inside an OU does not automatically grant or deny access to departmental documents.

### Principle of Least Privilege

Employees should receive only the access necessary to perform their authorized responsibilities.

For example, a Security Analyst may require access to security logs without needing Domain Administrator privileges.

### Role-Based Access Control

Security groups can support role-based access management by associating employees with permissions appropriate to their responsibilities.

However, membership alone does not prove that access permissions have been configured.

### Identity Lifecycle Management

When employees change departments, administrators should review their existing group memberships and remove access that is no longer necessary.

This helps prevent privilege accumulation and reduces the risk of unauthorized access.

### Security Monitoring and Accountability

Unique usernames help security analysts distinguish user accounts during investigations.

PowerShell and Active Directory administration tools can also be used to audit memberships and identify unexpected access assignments.

## 7. Challenges and Troubleshooting

During this lab, I encountered several situations that helped strengthen my understanding of Active Directory.

**Selecting multiple objects:** I initially opened a Properties window containing both a user and a security group. I learned to select the individual user account before modifying organizational attributes.

**Assigning security groups:** I initially needed guidance locating the correct field for entering a group name. I learned to use the Member Of tab, Check Names, and the group Members tab to configure and verify memberships.

**Understanding permissions:** I initially assumed that departmental OU placement could automatically restrict access to documents. I learned that actual resource permissions must be configured and verified separately.

**Verifying configuration:** Rather than relying only on the graphical interface, I used PowerShell to independently confirm the membership of all 15 employees.

## 8. Final Results

By the end of Day 3, I successfully:

- Created 15 employee accounts across four departments.
- Organized the accounts into their respective Active Directory OUs.
- Assigned all 15 employees to the appropriate departmental security groups.
- Verified each group's membership through Active Directory Users and Computers.
- Confirmed all four groups using Windows PowerShell.
- Improved my understanding of IAM, least privilege, RBAC, and identity lifecycle management.

**Scope limitation:** This lab verified identity provisioning and departmental group membership. Effective file access permissions, advanced administrative delegation, and authentication security controls remain subjects for future exercises.

## 9. Conclusion

Day 3 strengthened my practical understanding of how Active Directory supports identity management in a business environment.

The most important lesson was understanding the difference between **account organization, group membership, and actual resource permissions**.

I also learned that security analysts should investigate unexpected access before assuming it is malicious, because some access may have legitimate business justification or temporary authorization.

This lab provided a foundation for future Active Directory exercises involving access control, policy enforcement, auditing, and security investigations.
