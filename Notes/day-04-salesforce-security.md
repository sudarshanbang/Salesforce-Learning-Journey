# Day 04 — Salesforce Security, Users and Access Control

## Learning Objectives

- Salesforce security architecture
- Users
- Profiles
- Permission Sets
- Roles
- Organization-Wide Defaults (OWD)
- Sharing Rules
- Manual Sharing
- Field-Level Security (FLS)
- Object Permissions
- Login Hours and Login IP Ranges

---

# Salesforce Security Layers

```text
Organization
 ↓
Users
 ↓
Profiles
 ↓
Permission Sets
 ↓
Roles
 ↓
OWD
 ↓
Sharing Rules
 ↓
Manual Sharing
```

## Profiles
Profiles define what a user can do.

## Permission Sets
Permission Sets give extra permissions without changing a user's profile.

## Roles
Roles control record visibility.

## OWD
OWD defines default record access.

Options:
- Private
- Public Read Only
- Public Read/Write
- Controlled by Parent

## Sharing Rules
Automatically share records with users, roles, or groups.

## Manual Sharing
Share one record manually.

## Field-Level Security
Controls whether a field is visible or editable.

## Object Permissions
- Read
- Create
- Edit
- Delete
- View All
- Modify All

## Login Security
Profiles can define Login Hours and Login IP Ranges.

## Interview Questions
1. What is a Profile?
2. What is a Permission Set?
3. Difference between Profile and Permission Set?
4. What is a Role?
5. What is OWD?
6. What is Field-Level Security?
7. What is a Sharing Rule?
8. What is Manual Sharing?
9. What are Login Hours?
10. What are Login IP Ranges?

## Practical Tasks
- Explore Profiles
- Explore Permission Sets
- Explore Roles
- Explore Sharing Settings
- Explore Field-Level Security

## Key Takeaways
- Profiles define capabilities.
- Permission Sets extend access.
- Roles affect visibility.
- OWD is the baseline.
- Sharing Rules grant extra access.
- FLS protects sensitive fields.
