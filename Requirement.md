# Software Requirement Specification

## Overall Description

### Product Overview

This is the software requirement specification for the project "EduBlock". EduBlock is an web-application that will improve and increase the speed of work for school, more specifically, the students, teachers, staff and admin can reduce the paper's work for manage their records.  


### Business Rules

* The application will be used by the students, teachers, staff and admin.


## User Requirements
The Academic record management web-app has four active actors: Student, Teacher, Staff and Administrator.  

## Functional Requirements
### System Functional Overview
The system is designed to provide a platform for students to view their academic records, teachers to view their students’ academic records, staff to view the academic records of students, create new class.

### **Class Features**
#### UC-1 Get class list for Staff

* **Description:** Staff can get list of all classes .
* **Actors:** Staff
* **Preconditions:** Staff is logged in with staff account.
* **Postconditions:** Staff can get list of all classes.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * System displays list of all classes.
* **Alternate Flow:**
  * System displays error message if there is no class.
* **Exception Flow:**
  * System displays error message if there is no class.

#### UC-2 Get class list for Teacher

* **Description:** Teacher can get list of classes that he/she teach.
* **Actors:** Teacher
* **Preconditions:** Teacher is logged in with teacher account.
* **Postconditions:** Teacher can get list of classes that he/she teach.
* **Basic Flow:**
  * Teacher go to the web-app.
  * Teacher choose "Class Management" on menu
  * System displays list of classes that he/she teach.
* **Alternate Flow:**
  * System displays error message if there is no class.
* **Exception Flow:**
  * System displays error message if there is no class.

#### UC-3 Get class list for Student

* **Description:** Student can get list of classes he/she study.
* **Actors:** Student
* **Preconditions:** Student is logged in with student account.
* **Postconditions:** Student get list of classes that he/she study.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * System displays list of all classes.
* **Alternate Flow:**
  * System displays error message if there is no class.
* **Exception Flow:**
  * System displays error message if there is no class.

#### UC-4 Get homeroom class of teacher

* **Description:** Teacher can get list of their homeroom class.
* **Actors:** Teacher
* **Preconditions:** Teacher is logged in with teacher account.
* **Postconditions:** Teacher can get list of their homeroom class.
* **Basic Flow:**
  * Teacher go to the web-app.
  * Teacher choose "Class Management" on menu
  * Teacher choose filter "Homeroom class"
  * System displays list of their homeroom class.
* **Alternate Flow:**
  * System displays error message if there is no homeroom class.
* **Exception Flow:**
  * System displays error message if there is no homeroom class.

#### UC-5 Get class's detail

* **Description:** Staff, Teacher and Student can get detail of a class.
* **Actors:** Staff, Teacher, Student
* **Preconditions:** Staff, Teacher or Student is logged in with their account.
* **Postconditions:** Staff, Teacher or Student can get detail of a class.
* **Basic Flow:**
  * Staff, Teacher or Student go to the web-app.
  * Staff, Teacher or Student choose "Class Management" on menu
  * Staff, Teacher or Student choose a class
  * System displays detail of a class.
* **Alternate Flow:**
  * System displays error message if there is no class.
* **Exception Flow:**
  * System displays error message if there is no class.

#### UC-6 Create class

* **Description:** Only staff can create new class.
* **Actor:** Staff
* **Preconditions:** Staff is logged in with staff account.
* **Postconditions:** Staff success create new class.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * Staff click "Create Class" button
  * System displays form to create new class.
  * Staff fill in the form and click "Create" button.
  * Staff confirm the information.
  * System displays success message and new class has been created.
* **Alternate Flow:**
  * System displays error message if there is invalid class information.
* **Exception Flow:**
  * System displays error message if there is invalid class information.

#### UC-7 Update class

* **Description:** Staff can update class information.
* **Actor:** Staff
* **Preconditions:** 
  * Staff is logged in with staff account.
  * Class exists.
* **Postconditions:** Staff success update class information.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * Staff choose a class
  * Staff click "Update Class" button
  * Staff fill in the form and click "Update" button.
  * Staff confirm the information.
  * System displays success message and class information has been updated.
* **Alternate Flow:**
  * System displays error message if there is invalid class information
* **Exception Flow:**
  * System displays error message if there is invalid class information

#### UC-8 Get student list of class

* **Description:** Staff or Teacher can get list of students in a class.
* **Actors:** Staff, Teacher
* **Preconditions:** Staff or Teacher is logged in with their account.
* **Postconditions:** System display list of student in a class for Teacher or Staff.
* **Basic Flow:**
  * Staff or Teacher go to the web-app.
  * Staff or Teacher choose "Class Management" on menu
  * Staff or Teacher choose a class
  * Staff or Teacher click "Student List" button
  * System displays list of student in a class.
* **Alternate Flow:**
  * System displays message if there is no student in a class.
* **Exception Flow:**
  * System displays message if there is no student in a class.

#### UC-9 Get list of teachers of a class

* **Description:** Staff, Teacher or Student can get list of teachers of a class.
* **Actors:** Staff, Teacher, Student
* **Preconditions:** Staff, Teacher or Student is logged in with their account.
* **Postconditions:** System display list of teachers of a class for Staff, Teacher or Student.
* **Basic Flow:**
  * Staff, Teacher or Student go to the web-app.
  * Staff, Teacher or Student choose "Class Management" on menu
  * Staff, Teacher or Student choose a class
  * Staff, Teacher or Student click on "Teachers" 
  * System displays list of teachers of a class.
* **Alternate Flow:**
  * System displays message if there is no teacher in a class.
* **Exception Flow:**
  * System displays message if there is no teacher in a class.

#### UC-10 Assign teachers to a class

* **Description:** Staff can assign teachers to a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in with staff account.
  * Class exists.
  * Teacher exists.
* **Postconditions:** Staff success assign teachers to a class.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * Staff choose a class
  * Staff click "Assign Teachers"
  * System displays list of teachers for staff to choose.
  * Staff choose teachers and click on "Assign".
  * Staff confirm the action.
  * System displays success message and teachers have been assigned to a class.
* **Alternate Flow:**
  * System displays error message if there is no teacher chosen.
* **Exception Flow:**
  * System displays error message if there is no teacher chosen.

#### UC-11 Remove teachers from a class

* **Description:** Staff can remove teachers from a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in with staff account.
  * Class exists.
  * Teacher exists.
  * Teacher is assigned to a class.
* **Postconditions:** Staff success remove teachers from a class.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * Staff choose a class
  * Staff view list of teachers of a class.
  * Staff choose teachers and click on "Remove from class".
  * Staff confirm the action.
  * System displays success message and teachers have been removed from a class.
* **Alternate Flow:**
  * System displays error message
* **Exception Flow:**
  * System displays error message

#### UC-12 Add students to a class

* **Description:** Staff can add students to a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in with staff account.
  * Class exists.
  * Student exists.
* **Postconditions:** Staff success add students to a class.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * Staff choose a class
  * Staff click "Add Students"
  * System displays list of students for staff to choose.
  * Staff choose students and click on "Add".
  * Staff confirm the action.
  * System displays success message and students have been added to a class.
* **Alternate Flow:**
  * System displays error message if there's no student chosen.
* **Exception Flow:**
  * System displays error message.

#### UC-13 Remove students from a class

* **Description:** Staff remove students from a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in with staff account.
  * Class exists.
  * Student exists.
  * Student is assigned to a class.
* **Postconditions:** Staff success remove students from a class.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff choose "Class Management" on menu
  * Staff choose a class
  * Staff view list of students of a class.
  * Staff choose one or more students and click on "Remove from class".
  * Staff confirm the action.
  * System displays success message and students have been removed from a class.
* **Alternate Flow:**
  * System displays error message
* **Exception Flow:**
  * System displays error message

### **Account Features**

#### UC-14 Get own account information

* **Description:** User can get their own account information.
* **Actors:** Staff, Teachers, Users, Admin
* **Preconditions:** User is logged in with their account attached with their role.
* **Postconditions:** System display account information for User.
* **Basic Flow:**
  * User go to the web-app.
  * User login with their account.
  * User hover on their avatar at top right corner.
  * User click "Account Information".
  * System displays account information of the user.
* **Alternate Flow:**
  * System displays error message.
* **Exception Flow:**
  * System displays error message.

#### UC-15 List all account

* **Description:** Admin or Staff can get list of all accounts.
* **Actors:** Admin, Staff
* **Preconditions:** Admin or Staff is logged in with their account.
* **Postconditions:** System display list of all accounts for Admin or Staff.
* **Basic Flow:**
  * Admin or Staff go to the web-app.
  * Admin or Staff login with their account.
  * Admin or Staff click on "Account Management" on.
  * System displays list of all accounts.
* **Alternate Flow:**
  * System displays error message.
* **Exception Flow:**
  * System displays error message.

#### UC-16 Create one or multiple accounts

* **Description:** Admin is able to create one or multiple accounts.
* **Actors:** Admin
* **Preconditions:** Admin is logged in with their account.
* **Postconditions:** Admin success create one or multiple accounts.
* **Basic Flow:**
  * Admin go to the web-app.
  * Admin login with their account.
  * Admin click on "Account Management" on.
  * Admin click on "Create Account".
  * System displays form for Admin to fill in.
  * Admin fill in the form and click on "Create".
  * System displays success message and account has been created.
* **Alternate Flow:**
  * System displays error message if there is invalid input during the create process.
* **Exception Flow:**
  * System displays error message if there is invalid input during the create process.

#### UC-17 Update one or multiple account password

* **Description:** Admin is able to update one or multiple account password (Reset password).
* **Actors:** Admin
* **Preconditions:** 
  * Admin is logged in with their account.
  * Account must exist.
* **Postconditions:** Admin success update one or multiple account password.
* **Basic Flow:**
  * Admin go to the web-app.
  * Admin login with their account.
  * Admin click on "Account Management" on.
  * System displays list of all accounts.
  * Admin choose one or more accounts to update their password.
  * System displays form for Admin to fill in.
  * Admin fill in the form and confirm the change.
  * System displays success message and account password has been update.
* **Alternate Flow:**
  * System displays error message if there is invalid input during the update password process.
* **Exception Flow:**
  * System displays error message if there is invalid input during the update password process.

#### UC-18 Get list of accounts by role

* **Description:** Admin is able to get list of accounts with a specific role.
* **Actors:** Admin
* **Preconditions:** 
  * Admin is logged in with their account.
  * Account must exist.
  * Account must have a role.
* **Postconditions:** Admin success get list of accounts with a specific role.
* **Basic Flow:**
  * Admin go to the web-app.
  * Admin login with their account.
  * Admin click on "Account Management" on.
  * System displays list of all accounts.
  * Admin filter accounts's list by role.
  * System displays list of accounts with the chosen role.
* **Alternate Flow:**
  * System displays error message if there is no account with the chosen role.
* **Exception Flow:**
  * System displays error message if there is no account with the chosen role.

#### UC-19 Update user's profile

* **Description:** Staff is able to update user's profile.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in with their account.
  * User must exist.
* **Postconditions:** Staff success update user's profile.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff login with their account.
  * Staff click on "Account Management".
  * System displays list of all accounts .
  * Staff choose one account to update their profile.
  * System displays the profile for Staff to edit.
  * Staff edit information and confirm the change.
  * System displays success message and user's profile has been update.
* **Alternate Flow:**
  * System displays error message if there is invalid input during the edit process.
* **Exception Flow:**
  * System displays error message if there is invalid input during the edit process.

#### UC-20 User update their profile

* **Description:** Staff or admin is able to update their own profile.
* **Actors:** Staff, Admin
* **Preconditions:** 
  * Staff or Admin is logged in with their account.
* **Postconditions:** Staff or Admin success update their profile.
* **Basic Flow:**
  * Staff or Admin go to the web-app.
  * Staff or Admin login with their account.
  * Staff or Admin click on "Account Information".
  * System displays the profile of Staff or Admin.
  * Staff or Admin edit information and confirm the change.
  * System displays success message and user's profile has been update.
* **Alternate Flow:**
  * System displays error message if there is invalid input during the edit process.
* **Exception Flow:**
  * System displays error message if there is invalid input during the edit process.

#### UC-21 Update student information

* **Description:** Staff is able to update student information.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in with their account.
  * Student must exist.
* **Postconditions:** Staff success update student information.
* **Basic Flow:**
  * Staff go to the web-app.
  * Staff login with their account.
  * Staff click on "Student Management".
  * System displays list of all students.
  * Staff choose one student to update their information.
  * System displays the information.
  * Staff edit information and confirm the change.
  * System displays success message and student's information has been update.
* **Alternate Flow:**
  * System displays error message if there is invalid input during the update process.
* **Exception Flow:**
  * System displays error message if there is invalid input during the update process.

### Record Features

#### uc-22 Get own record

* **Description:** Student is able to get their own record.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in with their account.
* **Postconditions:** Student get their own record.
* **Basic Flow:**
  * 
* **Alternate Flow:**
  * 
* **Exception Flow:**

#### UC-23 Teacher get student's record

* **Description:** Teacher is able to view student's record.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in with their account.
  * Student must exist.
* **Postconditions:** Teacher get student's record.
* **Basic Flow:**
* **Alternate Flow:**
* **Exception Flow:**

#### UC-24 Request record update

* **Description:** Student or Teacher can request to update a record.
* **Actors:** Student, Teacher
* **Preconditions:** 
  * Student or Teacher is logged in with their account.
* **Postconditions:** Student or Teacher success to send request to update a record.
* **Basic Flow:**
* **Alternate Flow:**
* **Exception Flow:**

#### UC-25 Bulk request record update

* **Description:** Student or Teacher can request to update multiple records.
* **Actors:** Student, Teacher
* **Preconditions:** 
  * Student or Teacher is logged in with their account.
* **Postconditions:** Student or Teacher success to send request to update multiple records.
* **Basic Flow:**
* **Alternate Flow:**
* **Exception Flow:**

#### UC-26 Get list of records by class

* **Description:** Staff is able to get list of records by class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in with their account.
  * Class must exist.
  * Class must have students.
* **Postconditions:** Staff success to get list of records by class.
* **Basic Flow:**
* **Alternate Flow:**
* **Exception Flow:**



## Non-Functional Requirements

### External Interfaces

* Custom Fabric network

### Quality Attributes

Our application ensures the following quality attributes:

* **Usability:** The application is easy to use and understand. The application is designed to be intuitive and easy to use. The application is designed to be used by both teachers and students.
* **Reliability:** The application is designed to be reliable. The application is designed to be used with blockchain technology to ensure data integrity.
* **Performance:** The application is designed to be fast and responsive.
* **Security:** The application is designed to be secure. The application is designed to be used with blockchain technology to ensure data integrity.
* **Maintainability:** The application is designed to be easy to maintain, update, and extend.
* **Portability:** The application is designed to be portable.
* **Scalability:** The application is designed to be scalable and can be extended to support more users and more features.
* **Interoperability:** The application is designed to be interoperable with other applications.
* **Reusability:** The application is designed to be reusable.
* **Testability:** The application is designed to be easy to test.


## Other Requirements








