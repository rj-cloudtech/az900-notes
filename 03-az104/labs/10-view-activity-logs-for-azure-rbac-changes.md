# Exercise 10 View activity logs for Azure RBAC changes
- Learning path 2.: AZ-104: Manage identities and governance in Azure
- Module: 4. Secure your Azure resources with Azure role-based access control (Azure RBAC)

In deze oefening bekijk ik de Azure Activity Log voor RBAC wijzigingen via de Azure portal.

---

## Task 1 Activity log bekijken

Uitgevoerd via **Azure portal > All services > Activity log**

Filters ingesteld:
- Timespan: Last month
- Operation filter: role
- Geselecteerde operaties:
  - Create role assignment (roleAssignments)
  - Delete role assignment (roleAssignments)
  - Create or update custom role definition (roleDefinitions)
  - Delete custom role definition (roleDefinitions)

---

## Task 2 Log entry bekijken

De **Delete role assignment** entry geselecteerd en de details bekeken:

| Veld | Waarde |
|---|---|
| Operation name | Delete role assignment |
| Timestamp | Fri Apr 17 2026 20:50:52 GMT+0200 |
| Event initiated by | useraccountname |
| Role | Virtual Machine Contributor |
| Scope | Resource group: example-group-for-exercise-8 |
| Message | Shared with 'Chris Green' |
| Status | Succeeded |

---
