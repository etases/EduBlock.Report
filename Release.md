# Release Package & User Guides

## Deliverable Package

### Source Codes & Documents

|       No.        |       Items        |       Sub-Items        | Type | Version |
| :--------------: | :----------------: | :--------------------: | :--: | :-----: |
| **Code package** |                    |                        |      |         |
|        1         |      EduBlock      |    EduBlock Client     | New  |   1.0   |
|        2         | Blockchain Network |  Blockchain Chaincode  | New  |   1.0   |
|        3         |        OCR         | Record Table Processor | New  |   1.0   |
|   **Database**   |                    |                        |      |         |
|        1         |       Tables       |     `accounts.sql`     | New  |   1.0   |
|                  |                    |    `classrooms.sql`    | New  |   1.0   |
|                  |                    |     `subjects.sql`     | New  |   1.0   |
|  **Documents**   |                    |                        |      |         |
|        1         |    Requirement     |    `SRS_v1.0.docx`     | New  |   1.0   |
|        2         |     Deployment     | `UserGuide_v1.0.docx`  | New  |   1.0   |

### Known Issues, Limitations & Restrictions

## Installation Guides

### System Requirements

OS: any

CPU: at least 4 cores

RAM: at least 4Gb

NETWORK: required

SOFTWARE: Docker

### Setup Files

- `Dockerfile.backend`
- `Dockerfile.frontend`
- `Dockerfile.ocr`

### Installation Instruction

## User Manual

### Terms & Definitions

| No. | Term  | Definition |
| :-: | ----- | ---------- |
| 01  | F.FT  | Feature    |
| 02  | R.ADM | Admin      |
| 03  | R.STF | Staff      |
| 04  | R.TCH | Teacher    |
| 05  | R.STD | Student    |
| 06  | R.ANY | Any role   |

### System Requirements

OS: any

CPU: any

RAM: at least 1Gb

NETWORK: required

### Application Usage

#### Overview

| No. | Feature                      | Role                | Note                              |
| :-: | ---------------------------- | ------------------- | --------------------------------- |
| 01  | Create new account           | R.ADM               |                                   |
| 02  | View account list            | R.ADM, R.STF        |                                   |
| 03  | View profile                 | R.ANY               | Each role have different behavior |
| 04  | Update profile               | R.ADM, R.STF        | Each role have different behavior |
| 05  | Update password              | R.ANY               | Each role have different behavior |
| 06  | Create new classroom         | R.STF               |                                   |
| 07  | View classroom list          | R.STF, R.TCH, R.STD | Each role have different behavior |
| 08  | View classroom information   | R.STF, R.TCH, R.STD |                                   |
| 09  | View students of classroom   | R.STF, R.TCH, R.STD |                                   |
| 10  | View teachers of classroom   | R.STF, R.TCH, R.STD |                                   |
| 11  | Update classroom information | R.STF               |                                   |
| 12  | Update student in classroom  | R.STF               |                                   |
| 13  | Update teacher in classroom  | R.STF               |                                   |
| 14  | View update request list     | R.TCH               |                                   |
| 15  | Verify update request        | R.TCH               |                                   |
| 16  | Request update record        | R.TCH, R.STD        |                                   |

#### Feature 01: Create new account

**Description:**

- Admin create account for other user usage

**Details:**

- R.ADM
  - Step 1: Click <kbd>Account</kbd> on the left navigation bar to navigate to
    account list page
  - Step 2: Click <kbd>Create</kbd> at the top left of the page to open a modal
    with form
  - Step 3: Input user First name, Last name and select a role for user
  - Step 4: (Optional) Click <kbd>Add</kbd> at the bottom left of the form to
    add more account and repeat from Step 1
  - Step 5: Click <kbd>Create</kbd> at the bottom right of the form to confirm
    the account creation

#### Feature 02: View account list

**Description:**

- Admin, Staff view the account list to manage account information and find
  reference for other operations

**Details:**

- R.ADM
  - Step 1: Click <kbd>Account</kbd> on the left navigation bar to navigate to
    account list page
  - Step 2: (Optional) Click <kbd>Search</kbd> to reveal filter options below
  - Step 2.1: Select search field on the left
  - Step 2.2: Input search text on the right
  - Step 2.3: Click <kbd>Search</kbd> button at the right most to apply list
    filter
  - Step 3: View list of account
  - Step 4: (Optional) Click page number at the top right to view other accounts

#### Feature 03: View profile

**Description:**

- Admin, Staff view user profile
- User view personal profile

**Details:**

- R.ANY (Personal)
  - Step 1: Click personal card at the bottom of the Vertical Navigation bar to
    navigate to the profile page
- R.ADM, R.STF
  - Step 1: Click <kbd>Account</kbd> on the left navigation bar to navigate to
    account list page
  - Step 2: Look for the specific account row in table
  - Step 3: Click <kbd>Details</kbd> in the `Actions` column to navigate to the
    profile page of that account

#### Feature 04: Update profile

**Description:**

- Admin, Staff update personal profile
- Staff update Teacher, Student profile

**Details**

- R.ADM, R.STF (Personal)
  - Step 1: Click personal card at the bottom of the Vertical Navigation bar to
    navigate to the profile page
  - Step 2: Click <kbd>Update</kbd> in the profile section to open a modal with
    form
  - Step 3: Change the form data to desired value
  - Step 4: Click <kbd>Confirm</kbd> to save the changes.
- R.STF
  - Step 1: Click <kbd>Account</kbd> on the left navigation bar to navigate to
    account list page
  - Step 2: Look for the specific account row in table
  - Step 3: Click <kbd>Update</kbd> in the `Actions` column to open an update
    modal with form
  - Step 4: Change the form data to desired value
  - Step 5: Click <kbd>Confirm</kbd> to save the changes

#### Feature 05: Update password

**Description:**

- Admin update other user password
- User self update password

**Details**

- R.ANY (Personal)
  - Step 1: Click personal card at the bottom of the Vertical Navigation bar to
    navigate to the profile page
  - Step 2: Click <kbd>Update password</kbd> at the top right of the page to
    open a modal with form
  - Step 3: Input the new password
  - Step 4: Click <kbd>Confirm</kbd> to save the new password
- R.ADM
  - Step 1: Click <kbd>Account</kbd> on the left navigation bar to navigate to
    account list page
  - Step 2: Look for the specific account row in table
  - Step 3: Click <kbd>Update password</kbd> in the `Actions` column to open an
    update modal with form
  - Step 4: Input the new password
  - Step 5: Click <kbd>Confirm</kbd> to save the new password

#### Feature 06: Create new classroom

**Description:**

- Staff Create new classroom in the system

**Details**

- R.STF
  - Step 1: Click <kbd>Classroom</kbd> on the left navigation bar to navigate to
    classroom list page
  - Step 2: Click <kbd>Create</kbd> at the top left of the page to open a modal
    with form
  - Step 3: Change the form data to desired value
  - Step 4: Click <kbd>Confirm</kbd> at the bottom right of the modal to save
    the created classroom

#### Feature 07: View classroom list

**Description:**

- Staff view the list of all the classroom in the system
- Teacher view the list of all the classroom being taught by that teacher
- Student view the list of all the classroom that student taking part in

**Details**

- R.STF
  - Step 1: Click <kbd>Classroom</kbd> on the left navigation bar to navigate to
    classroom list page
- R.TCH, R.STD
  - Step 1: The list of classroom is in the dashboard page

#### Feature 08: View classroom information

**Description:**

- Staff view classroom information
- Teacher view information of the classroom being taught by that teacher
- Student view information of the classroom that student taking part in

**Details**

- R.STF
  - Step 1: Click <kbd>Classroom</kbd> on the left navigation bar to navigate to
    classroom list page
  - Step 2: Look for the specific classroom row in table
  - Step 3: Click <kbd>Details</kbd> in the `Actions` column to navigate to the
    classroom details page
- R.TCH, R.STD
  - Step 1: Click <kbd>Dashboard</kbd> on the left navigation bar to navigate to
    classroom list page
  - Step 2: Look for the specific classroom row in table
  - Step 3: Click <kbd>Details</kbd> in the `Actions` column to navigate to the
    classroom information page

#### Feature 09: View students of classroom

**Description:**

- Staff view all the student in a specific classroom
- Teacher view all the student in the classroom being taught by that teacher
- Student view all the student in the classroom that student taking part in

**Details**

- R.STF, R.TCH, R.STD
  - Step 1: Follow `Feature 08` to navigate to the classroom information page
  - Step 2: Click <kbd>Student</kbd> which is the center tab at the top of the
    page to navigate to student list of that classroom

#### Feature 10: View teachers of classroom

**Description:**

- Staff view all the teacher in a specific classroom
- Teacher view all the teacher in the classroom being taught by that teacher
- Student view all the teacher in the classroom that student taking part in

**Details**

- R.STF, R.TCH, R.STD
  - Step 1: Follow `Feature 08` to navigate to the classroom information page
  - Step 2: Click <kbd>Teacher</kbd> which is right most tab at the top of the
    page to navigate to teacher list of that classroom

#### Feature 11: Update classroom information

**Description:**

- Staff update a specific classroom information

**Details**

- R.STF
  - Step 1: Follow `Feature 08` to navigate to the classroom information page
  - Step 2: Click <kbd>Details</kbd> which is right most tab at the top of the
    page to navigate to details page of that classroom
  - Step 3: Click <kbd>Update</kbd> at the bottom of the page to open a modal
    with form
  - Step 4: Change the form data to desired value
  - Step 5: Click <kbd>Confirm</kbd> at the bottom of the modal to save changes

#### Feature 12: Update student in classroom

**Description:**

- Staff change the student of a specific classroom

**Details**

- R.STF
  - Step 1: Follow `Feature 09` to navigate to the classroom student page
  - Step 2: Look for a specific account row in the table (May skip to Step 4)
  - Step 3: Click <kbd>Remove</kbd> in the `Actions` column to remove student
    from classroom
  - Step 4: Click <kbd>Add</kbd> at the top left of the page to open a modal
    with form
  - Step 5: Change the form data to desired value
  - Step 6: Click <kbd>Confirm</kbd> at the bottom right of the modal to save
    changes

#### Feature 13: Update teacher in classroom

**Description:**

- Staff change the teacher of a specific classroom

**Details**

- R.STF
  - Step 1: Follow `Feature 10` to navigate to the classroom teacher page
  - Step 2: Look for a specific account row in the table (May skip to Step 4)
  - Step 3: Click <kbd>Remove</kbd> in the `Actions` column to remove teacher
    from classroom
  - Step 4: Click <kbd>Add</kbd> at the top left of the page to open a modal
    with form
  - Step 5: Change the form data to desired value
  - Step 6: Click <kbd>Confirm</kbd> at the bottom right of the modal to save
    changes

#### Feature 14: View update request list

**Description:**

- Teacher view list of request for updating record value

**Details**

- R.TCH
  - Step 1: Click <kbd>Request</kbd> on the left navigation bar to navigate to
    request list page

#### Feature 15: Verify update request

**Description:**

- Teacher verify request waiting for verification

**Details**

- R.TCH
  - Step 1: Follow `Feature 14` to navigate to the request list page
  - Step 2: Look for the specific request row in table
  - Step 3: Click <kbd>Approve</kbd> or <kbd>Reject</kbd> to approve or reject
    the request

#### Feature 16: Request update record

**Description:**

- Teacher or student of same classroom request updating record for that student

**Details**

- R.TCH
  - Step 1: Follow `Feature 09` to navigate to student profile page
  - Step 2: Look for the record need update in the record table at the bottom of
    the page
  - Step 3: Click <kbd>Update</kbd> in the `Actions` column to open a modal with
    form
  - Step 4: Change the form data to desired value
  - Step 5: Click <kbd>Confirm</kbd> to send the request
- R.STD
  - Step 1: Click personal card at the bottom of the Vertical Navigation bar to
    navigate to the profile page
  - Step 2: Look for the record need update in the record table at the bottom of
    the page
  - Step 3: Click <kbd>Update</kbd> in the `Actions` column to open a modal with
    form
  - Step 4: Change the form data to desired value
  - Step 5: Click <kbd>Confirm</kbd> to send the request

### Troubleshooting
