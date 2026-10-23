# Day 2 — Organizing Chaos: Active Directory OUs and Security Groups

## Project Overview

On Day 2 of my TotalThreat Active Directory Home Lab, I focused on organizing my Windows Server Active Directory environment by creating Organizational Units (OUs) and departmental security groups.

After configuring the NMG.com domain during Day 1, my objective was to simulate a real company's departmental structure and understand how administrators organize accounts and manage access permissions.

This lab introduced fundamental cybersecurity concepts, including Identity and Access Management (IAM), Role-Based Access Control (RBAC), and the principle of least privilege.

## Lab Environment

- **Virtualization:** Oracle VirtualBox
- **Operating System:** Windows Server
- **Domain:** NMG.com
- **Administrative Tool:** Active Directory Users and Computers (ADUC)
- **Environment:** Cybersecurity Home Lab

## Lab Objectives

1. Create four departmental Organizational Units.
2. Create departmental security groups.
3. Configure Global security groups.
4. Understand the difference between OUs and security groups.
5. Explore centralized access management.
6. Verify and document the configuration.

---

## Step 1 — Creating Organizational Units

I opened Active Directory Users and Computers and navigated to the NMG.com domain.

I created four Organizational Units:

- Finance
- HR
- IT
- Operations

Each OU represents a department in the simulated organization.

### Screenshot 1 — Creating the Finance OU

![Finance Organizational Unit](screenshots/01-finance-ou.png)

*Figure 1: The Finance Organizational Unit successfully created under the NMG.com domain.*

This was the first step in establishing a departmental structure in Active Directory.

### Screenshot 2 — Final Organizational Unit Structure

![Four Organizational Units](screenshots/02-all-organizational-units.png)

*Figure 2: The Finance, HR, IT, and Operations Organizational Units organized under NMG.com.*

### Why Organizational Units Matter

Organizational Units allow administrators to organize accounts and other Active Directory objects logically.

They also support:

- Department-specific Group Policies
- Delegation of administrative responsibilities
- Centralized account management
- Simplified Active Directory administration

---

## Step 2 — Creating Departmental Security Groups

After creating the Organizational Units, the next task was to create security groups inside their respective departments.

The lab configuration uses:

| Department | Security Group | Scope | Type |
|---|---|---|---|
| Finance | Finance-Users | Global | Security |
| HR | HR-Users | Global | Security |
| IT | IT-Users | Global | Security |
| Operations | Operations-Users | Global | Security |

### Screenshot 3 — Finance Security Group

![Finance Security Group](screenshots/03-finance-security-group.png)

*Figure 3: Finance-Users security group created inside the Finance OU.*

The Finance-Users group provides a way to manage permissions collectively for authorized Finance employees.

### Screenshot 4 — HR Security Group

![HR Security Group](screenshots/04-hr-security-group.png)

*Figure 4: HR-Users security group created inside the HR OU.*

This group can be used to manage permissions for authorized Human Resources employees.

### Screenshot 5 — IT Security Group

![IT Security Group](screenshots/05-it-security-group.png)

*Figure 5: IT-Users security group created inside the IT OU.*

This group can be used to manage permissions for IT personnel.

### Screenshot 6 — Operations Security Group

![Operations Security Group](screenshots/06-operations-security-group.png)

*Figure 6: Operations-Users security group created inside the Operations OU.*

This group can be used to manage permissions for authorized Operations employees.

### Why Security Groups Matter

Security groups allow administrators to assign resource permissions to groups instead of individual users.

For example, instead of configuring access separately for 20 Finance employees, an administrator can assign the appropriate permissions to Finance-Users.

Members of that group can then receive those permissions, subject to the applicable access controls.

This approach improves scalability, consistency, and administrative efficiency.

---

## Step 3 — Understanding OUs vs. Security Groups

One of the most important lessons from this lab was understanding the difference between Organizational Units and security groups.

**Organizational Units:**

- Organize Active Directory objects.
- Support Group Policy application.
- Allow delegation of administrative responsibilities.

**Security Groups:**

- Group accounts for permission assignments.
- Simplify access management.
- Support group-based authorization.

For example, placing an employee in the Finance OU does not automatically grant access to financial reports.

That access must be configured through appropriate permissions, which may be assigned to the Finance-Users security group.

---

## Step 4 — Cybersecurity Knowledge Assessment

### Question 1: Why place an employee in the Finance OU instead of HR?

An employee should be placed in the Finance OU because their responsibilities involve financial operations such as accounting, payroll, and budgeting.

Departmental OUs help administrators organize accounts, apply appropriate Group Policies, and delegate administration.

### Question 2: What happens when a user is added to Finance-Users?

The user becomes a member of the Finance-Users security group and can receive permissions assigned to that group.

This allows administrators to manage access centrally rather than configuring individual permissions for every employee.

### Question 3: Which group should manage access to Finance reports?

I would use Finance-Users because it represents authorized Finance employees.

By assigning appropriate permissions to this group, administrators can manage access to shared financial documents collectively.

### Question 4: Why manage permissions through security groups?

Managing access through security groups is more efficient, scalable, and consistent.

Administrators can add or remove group members as employee responsibilities change without repeatedly modifying resource permissions.

This approach can also support the principle of least privilege.

---

## Key Cybersecurity Concepts Learned

**Identity and Access Management (IAM):** Managing identities and controlling access to organizational resources.

**Role-Based Access Control (RBAC):** Assigning access based on defined organizational responsibilities.

**Principle of Least Privilege:** Granting users only the access required for their authorized responsibilities.

**Centralized Administration:** Managing accounts, groups, and policies from a central directory.

**Group-Based Access Management:** Assigning permissions to groups instead of managing each user individually.

---

## Challenges and Lessons Learned

This lab helped me understand that organizing Active Directory accounts and granting permissions are two different administrative responsibilities.

Organizational Units provide structure and help administrators apply policies, while security groups are used to manage access permissions.

I also learned that creating a security group does not automatically provide access to resources. Permissions must be configured separately.

The biggest takeaway was understanding how group-based administration can improve efficiency while supporting consistent security practices.

---

## Conclusion

Day 2 focused on establishing the organizational structure of my Active Directory environment.

By creating departmental Organizational Units and configuring security groups, I developed a better understanding of centralized identity administration and access management.

This foundation will support future exercises involving user account creation, Group Policy, access control, and Active Directory security.

**Project:** TotalThreat Active Directory Home Lab  
**Day:** 2 — Organizing Chaos  
**Domain:** NMG.com
