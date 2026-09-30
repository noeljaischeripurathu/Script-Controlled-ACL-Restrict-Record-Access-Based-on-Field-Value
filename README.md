# Script-Controlled ACL – Restrict Record Access Based on Field Value

A ServiceNow micro project that uses **script-controlled Access Control Lists (ACLs)** to restrict who can **read, create, write and delete** records in a custom table, based on the value of the **Branch** field. Only users holding the right custom roles can see **EEE** branch records, while administrators retain full access.

## Team Members
| S.No | Name | Reg No | Department |
|------|------|--------|------------|
| 1 | Noel Jais | C4S32208 | Physics |
| 2 | Nisha Devi P | C4S32202 | Physics |
| 3 | Selvinkumar S | C4S32210 | Physics |

**College:** Mary Matha College of Arts and Science, Periyakulam, Theni

## Links
- **GitHub Repository:** https://github.com/noeljaischeripurathu/Script-Controlled-ACL-Restrict-Record-Access-Based-on-Field-Value
- **Demo Video:** https://drive.google.com/file/d/1otBEL14NNOl1m77vg9nPVpjpeB7yMm5c/view?usp=drivesdk

## Table of Contents
1. [Project Overview](#project-overview)
2. [Objectives](#objectives)
3. [Problem Statement](#problem-statement)
4. [Solution Summary](#solution-summary)
5. [Project Phases](#project-phases)
6. [Tech Stack](#tech-stack)
7. [Key Components](#key-components)
8. [Repository Structure](#repository-structure)
9. [How to Reproduce the Lab](#how-to-reproduce-the-lab)
10. [Expected Results](#expected-results)
11. [Learning Outcomes](#learning-outcomes)

## Project Overview
ServiceNow protects data through Access Control Lists. An ACL decides whether a user may perform an operation (read, write, create, delete) on a table, a record or a field. This project builds a real example: a table of student records where each record belongs to a branch (ECE, EEE or CSE), and access is tightly controlled using roles, a data condition and a server-side script.

## Objectives
- Create a test user and four custom roles (bb1, bb2, bb3, bb4).
- Create a custom table `u_institution_details` to hold student records.
- Build a **Read ACL** that combines a role, a data condition (Branch is EEE) and an advanced script.
- Build **Create**, **Write** and **Delete** ACLs, each tied to its own role.
- Verify the behaviour by impersonating an EEE user, a user without roles and an admin.

## Problem Statement
When student records of several branches live in one table, any user who can open the table could view or change every branch's data. This creates privacy and data-integrity risks. The institution needs branch-level, role-based control that is enforced on the **server**, not just hidden in the interface.

## Solution Summary
| Operation | Role required | Extra condition |
|-----------|---------------|-----------------|
| Read | bb1 | Data condition **Branch is EEE** + advanced script |
| Create | bb2 | None |
| Write | bb3 | None |
| Delete | bb4 | None |

Admins pass every ACL because **Admin overrides** is enabled and the read script also explicitly allows `admin`.

## Project Phases
| # | Phase | Folder |
|---|-------|--------|
| 1 | Brainstorming & Ideation | [1-Brainstorming-Ideation](1-Brainstorming-Ideation/) |
| 2 | Requirement Analysis | [2-Requirement-Analysis](2-Requirement-Analysis/) |
| 3 | Project Design | [3-Project-Design](3-Project-Design/) |
| 4 | Project Planning | [4-Project-Planning](4-Project-Planning/) |
| 5 | Project Development | [5-Project-Development](5-Project-Development/) |
| 6 | Project Testing | [6-Project-Testing](6-Project-Testing/) |
| 7 | Project Documentation | [7-Project-Documentation](7-Project-Documentation/) |
| 8 | Project Demonstration | [8-Project-Demonstration](8-Project-Demonstration/) |

## Tech Stack
| Item | Detail |
|------|--------|
| Platform | ServiceNow (Global application scope) |
| Security feature | Access Control (ACL) |
| Scripting | Server-side JavaScript using `gs.hasRole()` |
| Custom table | `u_institution_details` (label: Institution Details) |
| Elevated role used | `security_admin` |
| Testing method | User impersonation |

## Key Components
- **User:** EEE User (User ID `EEEUser`)
- **Roles:** bb1 (read), bb2 (create), bb3 (write), bb4 (delete)
- **Table:** Institution Details (`u_institution_details`)
- **Fields:** Student Roll Number, Student Name, Faculty Name, Branch, Email, Phone Number, Description
- **ACLs:** Read (with data condition and script), Create, Write, Delete

## Repository Structure
```
Script-Controlled-ACL-Restrict-Record-Access-Based-on-Field-Value/
├── README.md
├── 1-Brainstorming-Ideation/
│   └── Brainstorming_and_Ideation.md
├── 2-Requirement-Analysis/
│   └── Requirement_Analysis.md
├── 3-Project-Design/
│   └── Project_Design.md
├── 4-Project-Planning/
│   └── Project_Planning.md
├── 5-Project-Development/
│   ├── Development_Steps.md
│   ├── scripts/read_acl_script.js
│   └── screenshots/  (28 step-by-step screenshots)
├── 6-Project-Testing/
│   └── Test_Cases.md
├── 7-Project-Documentation/
│   ├── README.md
│   └── Script-Controlled_ACL-Micro_Projects.pdf
└── 8-Project-Demonstration/
    └── Demonstration.md
```

## How to Reproduce the Lab
1. Create the EEE User and roles bb1–bb4 and assign the roles (Phase 5, Milestone 1).
2. Create the `u_institution_details` table, add the fields and insert sample records (Milestone 2).
3. Elevate to `security_admin` and create the four ACLs (Milestones 3–6).
4. Impersonate each user type and check the results (Phase 6).

## Expected Results
- A user with **bb1** sees **only EEE** records.
- A user with **no roles** sees **no records**.
- An **admin** sees **all records**.
- **bb2** adds the **New** button, **bb3** allows **editing**, **bb4** allows **deleting**.

## Learning Outcomes
- Understand how READ, WRITE, CREATE and DELETE ACLs enforce record-level security.
- Learn how roles, data conditions and scripts are evaluated together.
- Learn how ACLs protect sensitive data in forms, lists and portals.
- Practise testing security through impersonation.
