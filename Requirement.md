# Software Requirement Specification

## Overall Description

### Product Overview

This is the software requirement specification for the project "EduBlock". EduBlock is an web-application that will help the school to manage their student's records, more specifically, the students and teachers can reduce paper's work to manage their records. Lately, the school has been using paper to manage their student's record, which is not efficient and not environmental friendly. EduBlock will help the school to manage their student's records in a more efficient way, although there are some other 3rd party applications that can help school to keep their student's records, but it is not really efficient and safe, our application use blockchain technology to make sure the data is safe and secure. Every step of the process that need to be work with the records will be tracked by EduBlock, so the school can easily track the data and make sure the data is not being tampered.  


### Business Rules

* The application will be used by the students, teachers, staff and admin.


## User Requirements
* The Academic record management web-app has four active actors: Student, Teacher, Staff and Administrator.
* Students can view their academic record.
* Teachers can manage their class and view their students' academic record.
* Staff can manage the classroom and view the academic record of the students, assign or delete teacher from the class, assign student to class, create new class.

## Functional Requirements
### System Functional Overview
The system is designed to provide a platform for students to view their academic records, teachers to view their students’ academic records, staff to view the academic records of students, create new class.

### **Admin Features**
#### UC-1 Admin Login

* **Description:** Admin can login with their username and password.
* **Actors:** Admin.
* **Preconditions:** Admin has an account.
* **Postconditions:** Admin can access the system.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin enters their username and password.
  * System verifies the username and password.
  * System displays the dashboard.
* **Exceptions:**
  * If the username or password is incorrect, the system will display an error message.

#### UC-2 Admin view list of accounts

* **Description:** Admin can view list of all accounts.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System show list of all accounts.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on “Account”.
  * System show list of all accounts.
* **Alternate Flow:**
  * System displays notification “No account found” if there is no account.
* **Exception:**
  * System displays notification “No account found” if there is no account.

#### UC-3 Admin view account details

* **Description:** Admin can view account details.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System show account details.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on “Account”.
  * Admin click on "Details" (human icon) on actions column.
  * System show account details.
* **Alternate Flow:**
  * System displays notification “No account found” if there is no account.
* **Exception:**
  * System displays notification “No account found” if there is no account.

#### UC-4 Admin create (multiple) account

* **Description:** Admin can create (multiple) account for each role such as staff, student, teacher.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System create (multiple) account.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on “Account”.
  * Admin click on “Create” button.
  * Admin fill in the form.
  * Admin can click "Add Account" button to add more account.
  * Admin click on “Create” button.
  * System create account(s).
* **Alternate Flow:**
  * System displays notification if the form is not filled correctly.
* **Exception:**
  * System displays notification if the form is not filled correctly.

#### UC-5 Admin search account

* **Description:** Admin can search account by text, username, email, id, first name and last name.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System show list of accounts that match the search criteria.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on “Account”.
  * Admin click on “Search” button.
  * Admin input text to search account.
  * Admin add search criteria.
  * System show list of accounts that match the search criteria.
* **Alternate Flow:**
  * System displays notification “No account found” if there is no account that match the search criteria.
* **Exception:**
  * System displays notification “No account found” if there is no account that match the search criteria.

### **Staff Features**
#### UC-6 Staff Login

* **Description:** Staff can login with their username and password.
* **Actors:** Staff.
* **Preconditions:** Staff has an account.
* **Postconditions:** Staff can access the system.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff enters their username and password.
  * System verifies the username and password.
  * System redirect Staff to dashboard.
* **Exceptions:**
  * If the username or password is incorrect, the system will display an error message.

#### UC-7 Staff view list of accounts

* **Description:** Staff can view list of all accounts.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System show list of all accounts.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Account”.
  * System show list of all accounts.
* **Alternate Flow:**
  * System displays notification “No account found” if there is no account.
* **Exception:**
  * System displays notification “No account found” if there is no account.

#### UC-8 Staff view account list by role

* **Description:** Staff can view list of accounts by role.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System show list of accounts by role.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Account”.
  * Staff click on role's name to view list of accounts by role.
  * System show list of accounts by role.
* **Alternate Flow:**
  * System displays notification “No account found” if there is no account.
* **Exception:**
  * System displays notification “No account found” if there is no account.

#### UC-9 Staff view account details

* **Description:** Staff can view account details.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System show account details.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Account”.
  * Staff click on "Details" (human icon) on actions column.
  * System show account details.
* **Alternate Flow:**
  * System displays notification “No account found” if there is no account.
* **Exception:**
  * System displays notification “No account found” if there is no account.

#### UC-10 Staff search account

* **Description:** Staff can search account by text, username, email, id, first name and last name.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System show list of accounts that match the search criteria.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Account”.
  * Staff click on “Search” button.
  * Staff input text to search account.
  * Staff add search criteria.
  * System show list of accounts that match the search criteria.
* **Alternate Flow:**
  * System displays notification “No account found” if there is no account that match the search criteria.
* **Exception:**
  * System displays notification “No account found” if there is no account that match the search criteria.

#### UC-11 Staff view class list

* **Description:** Staff can view list of all classes.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System show list of all classes.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * System show list of all classes.
* **Alternate Flow:**
  * System displays notification “No class found” if there is no class.
* **Exception:**
  * System displays notification “No class found” if there is no class.



### **Teacher Features**

### **Student Features**

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








