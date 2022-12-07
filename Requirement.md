# Software Requirement Specification

## Overall Description

### Product Overview

This is the software requirement specification for the project "EduBlock". EduBlock is an web-application that will help the school to manage their student's records, more specifically, the students and teachers can reduce paper's work to manage their records. Lately, the school has been using paper to manage their student's record, which is not efficient and not environmental friendly. EduBlock will help the school to manage their student's records in a more efficient way, although there are some other 3rd party applications that can help school to keep their student's records, but it is not really efficient and safe, our application use blockchain technology to make sure the data is safe and secure. Every step of the process that need to be work with the records will be tracked by EduBlock, so the school can easily track the data and make sure the data is not being tampered.  


### Business Rules

* The application will be used by the students, teachers, staff and admin.
* Staff can't do any action on accounts but can do with classes.


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

#### UC-6 Admin update their profile

* **Description:** Admin can update their profile's information.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System update admin's profile.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admmin click on their avatar above logout button at bottom left.
  * Admin click on "Update" button at top right corner.
  * A form will appear, admin then input their new information.
  * Admin click "Submit".
  * System update admin's information and show success message.
* **Alternate Flow:**
  * System displays notification if the form is not filled correctly.
* **Exception:**
  * System displays notification if the form is not filled correctly.


### **Staff Features**
#### UC-7 Staff Login

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

#### UC-8 Staff view list of accounts

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

#### UC-10 Staff view account details

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

#### UC-11 Staff search account

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

#### UC-12 Staff view class list

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

#### UC-13 Staff create new class

* **Description:** Staff create a new class.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System create a new class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on “Create” button.
  * A form will appear, staff then input class's information.
  * Staff click "Create classroom".
  * System create a new class and show success message.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### UC-14 Staff view class details

* **Description:** Staff view details of a class.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System show class details.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (details icon) on actions column.
  * System show class details.
* **Alternate Flow:**
  * System displays notification “No class found” if there is no class.
* **Exception:**
  * System displays notification “No class found” if there is no class.

#### UC-15 Staff edit class

* **Description:** Staff edit class's information.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System edit class's information.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Update details".
  * A form will appear, staff then edit class's information.
  * System edit class's information and show success message.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### UC-16 Staff view student of a class

* **Description:** Staff view list of students in a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
* **Postconditions:** System show list of students in a class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Students".
  * System show list of students of the class.
* **Alternate Flow:**
  * System displays notification “No student found” if there is no student in the class.
* **Exception:**
  * System displays notification “No student found” if there is no student in the class.

#### UC-17 Staff add students to a class

* **Description:** Staff add students to a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
* **Postconditions:** System add students to a class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Students".
  * System show list of students of the class.
  * Staff click "Add students".
  * A form will appear, staff then choose students to add to the class.
  * Staff click "Add student" to add more students.
  * Staff click "Confirm".
  * System add student(s) to the class and show success message.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
  * System displays error notification if the student is already in the class.
  * System displays error notification if no student is selected.
* **Exception:**
  * System displays error notification if the form is not filled correctly.
  * System displays error notification if the student is already in the class.
  * System displays error notification if no student is selected.

#### UC-18 Staff view student details

* **Description:** Staff view details of a student.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Student exists.
  * Student is in a class.
* **Postconditions:** System show student details.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Students".
  * System show list of students of the class.
  * Staff click "Details" (icon) on actions column.
  * System show student details.
* **Alternate Flow:**
  * System displays notification “No student found” if there is no student in the class.
* **Exception:**
  * System displays notification “No student found” if there is no student in the class.

#### UC-19 Staff edit student information

* **Description:** Staff edit student's information.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Student exists.
  * Student is in a class.
* **Postconditions:** System edit student's information.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Students".
  * System show list of students of the class.
  * Staff click "Details" (icon) on actions column.
  * System show student details.
  * Staff click "Update" button.
  * A form will appear, staff then edit student's information.
  * System edit student's information and show success message.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### UC-20 Staff remove student from a class

* **Description:** Staff remove student from a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
  * Student exists.
  * Student is in a class.
* **Postconditions:** System remove student from the class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Students".
  * System show list of students of the class.
  * Staff click "Remove" (icon) on actions column.
  * System remove student from the class and show success message.
* **Alternate Flow:**
  * System displays error notification if the student is not in the class.
* **Exception:**
  * System displays error notification if the student is not in the class.

#### UC-21 Staff view teacher of a class

* **Description:** Staff view list of teachers in a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
* **Postconditions:** System show list of teachers in a class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Teachers".
  * System show list of teachers of the class.
* **Alternate Flow:**
  * System displays notification “No teacher found” if there is no teacher in the class.
* **Exception:**
  * System displays notification “No teacher found” if there is no teacher in the class.

#### UC-22 Staff assign teacher(s) to a class

* **Description:** Staff assign teacher(s) to a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
* **Postconditions:** System assign teacher(s) to a class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Teachers".
  * System show list of teachers of the class.
  * Staff click "Add teachers".
  * A form will appear, staff then choose teachers and their subjects.
  * Staff click "Add teacher" to add more teachers.
  * Staff click "Confirm".
  * System add teacher(s) to the class and show success message.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
  * System displays error notification if the teacher is already in the class.
  * System displays error notification if no teacher is selected.
  * System displays error notification if no subject is selected.
* **Exception:**
  * System displays error notification if the form is not filled correctly.
  * System displays error notification if the teacher is already in the class.
  * System displays error notification if no teacher is selected.
  * System displays error notification if no subject is selected.

#### UC-23 Staff remove teacher from a class

* **Description:** Staff remove teacher from a class.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
  * Teacher exists.
  * Teacher is in a class.
* **Postconditions:** System remove teacher from the class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Teachers".
  * System show list of teachers of the class.
  * Staff click "Remove" (icon) on actions column.
  * System remove teacher from the class and show success message.
* **Alternate Flow:**
  * System displays error notification if the teacher is not in the class.
* **Exception:**
  * System displays error notification if the teacher is not in the class.

#### UC-24 Staff edit their profile

* **Description:** Staff edit their profile.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
* **Postconditions:** System edit staff's profile.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on their avatar at bottom left of screen.
  * System display staff's profile.
  * Staff click "Update" button.
  * A form will appear, staff then edit their information.
  * Staff click "Submit" button.
  * System edit staff's information and show success message.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

### **Teacher Features**

#### UC-25 Teacher Login

* **Description:** Teacher login to EduBlock.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher has an account.
* **Postconditions:** System login teacher to EduBlock.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher go to login page.
  * Teacher enter username and password.
  * Teacher click "Login" button.
  * System authorize and login teacher to EduBlock.
* **Alternate Flow:**
  * System displays error notification if the username or password is incorrect.
* **Exception:**
  * System displays error notification if the username or password is incorrect.

#### UC-26 Teacher view their profile

* **Description:** Teacher view their profile.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
* **Postconditions:** System display teacher's profile.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * Teacher click on their avatar at bottom left of screen.
  * System display teacher's profile.


#### UC-27 Teacher view their classes

* **Description:** Teacher view their classes.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
* **Postconditions:** System display teacher's classes.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On login succes, system will redirect teach to dashboard where their classes will be display.
* **Alternate Flow:**
  * System displays notification “No class found” if there is no class.
* **Exception:**
  * System displays notification “No class found” if there is no class.

#### UC-28 Teacher class details

* **Description:** Teacher view class details.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Class exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
* **Postconditions:** System display class details.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * At dashboard Teacher click on "Details" (icon) on actions column.
  * System show class details.
* **Alternate Flow:**
  * System displays error notification if the class is not found.
* **Exception:**
  * System displays error notification if the class is not found.

#### UC-29 Teacher view students in a class

* **Description:** Teacher view list of students in a class.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Class exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
* **Postconditions:** System show list of students in a class.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Students".
  * System show list of students of the class.
* **Alternate Flow:**
  * System displays notification “No student found” if there is no student in the class.
* **Exception:**
  * System displays notification “No student found” if there is no student in the class.

#### UC-30 Teacher view teachers in the class

* **Description:** Teacher view list of teachers in the class.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Class exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
* **Postconditions:** System show list of teachers in the class.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Teachers".
  * System show list of teachers of the class.
* **Alternate Flow:**
  * System displays notification “No teacher found” if there is no teacher in the class.
* **Exception:**
  * System displays notification “No teacher found” if there is no teacher in the class.

#### UC-31 Teacher view Student details

* **Description:** Teacher view student details.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** System show student details.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Students".
  * System show list of students of the class.
  * Teacher click "Details" (icon) on actions column.
  * System show student details.
* **Alternate Flow:**
  * System displays "Student not found" if no student in class.
* **Exception:**
  * System displays "Student not found" if no student in class.

#### UC-32 Teacher export student's records to pdf

* **Description:** Teacher export student's records to pdf.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** System export student's records to pdf.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard (*classroom list*) Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Students".
  * System show list of students of the class.
  * Teacher click "Details" (icon) on actions column.
  * System show student details.
  * Teacher click "Print Record" button at Record session of student profile.
  * System show export preview of student's records.
  * Teacher click "Save" button.
  * System save student's records to teacher's computer as pdf.

#### UC-33 Subject teacher send request to edit student's grade

* **Description:** Subject teacher send request to edit student's grade.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** System send request to edit student's grade.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard (*classroom list*) Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Students".
  * System show list of students of the class.
  * Teacher click "Details" (icon) on actions column.
  * System show student details.
  * Teacher click "Request Update" (icon) on Action column at Record session of student profile.
  * System show edit grade form.
  * Teacher fill the form and click "Request" button.
  * System send request to edit student's grade.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### UC-34 Teacher upload legacy Record

#### UC-35 Teacher view list pf Pending Records's Request and Approve or Reject

* **Description:** Teacher view list of pending records's request.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
  * Subject teacher sent request to edit student's grade.
* **Postconditions:** System show list of pending records's request.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * Teacher click on "Pending Verification" button at sidebar.
  * System show list of pending records's request.
  * Teacher click "Approve" (check icon) on Action column to approve the request.
  * System approve the request.
* **Alternate Flow:**
  * Teacher click "Reject" (close icon) on Action column to reject the request.
  * System reject the request.
* **Exception:**
  * System displays "No pending request" if there is no pending request.

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








