# Software Requirement Specification

## Overall Description

### Product Overview

This is the software requirement specification for the project "EduBlock". EduBlock is an web-application that will help the school to manage their student's records, more specifically, the students and teachers can reduce paper's work to manage their records. Lately, the school has been using paper to manage their student's record, which is not efficient and not environmental friendly. EduBlock will help the school to manage their student's records in a more efficient way, although there are some other 3rd party applications that can help school to keep their student's records nowdays, but it is not really efficient and safe, our application use blockchain technology to make sure the data is safe and secure. Every step of the process that need to be work with the records will be tracked by EduBlock, so the school can easily track the data changes and make sure the data is not being tampered.  


### Business Rules

| **ID** | **Rules Description**                                                                                                                                                                                                     |
| :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| BR-1   | The application will be used by the students, teachers, staff and admin.                                                                                                                                                  |
| BR-2   | Only Staff have permission to manage classroom including create new class, edit class, assign or remove teacher from the class, assign student to class, remove student from class.                                       |
| BR-3   | Only Admin have permission to manage account including create new account, edit account                                                                                                                                   |
| BR-4   | Only Teacher who teach the subject can edit the grade of the student.                                                                                                                                                     |
| BR-5   | Student can only view their class, profile and academic record.                                                                                                                                                           |
| BR-6   | In Blockchain, the data is immutable, so the data cannot be changed once it is created. Because of this, the data can just be append, can't be edit or delete, this will help ensure student's record is safe and secure. |
| BR-7   | A node if want to join the network, it must have other nodes permission or the node must be approved by the admin.                                                                                                        |
| BR-8   | In private blockchain, every node know each other, which node own the data. Data is shared between nodes so the data can be recovered if one node is down.                                                                |
| BR-9   | Other nodes can only read the data, they cannot change the data.                                                                                                                                                          |




## User Requirements
* The Academic record management web-app has four active actors: Student, Teacher, Staff and Administrator.
* Students can view their academic record.
* Teachers can manage their class and view their students' academic record.
* Staff can manage the classroom and view the academic record of the students, assign or delete teacher from the class, assign student to class, create new class.

### a. System Actors

| **ID** | **Actor** | **Description**                                                                                                                                                              |
| :----- | :-------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1      | ADMIN     | Admin is the person who has the highest authority in the system. Admin can manage the account of the other actors.                                                           |
| 2      | STAFF     | Staff is the person who has the authority to manage the classroom. Staff can assign or remove teacher from the class, assign student to class, remove student from class.    |
| 3      | TEACHER   | Teacher is the person who has the authority to manage their class. Teacher can view their students' academic record, subject teacher can send request to edit student grade. |
| 4      | STUDENT   | Student is the person who has the authority to view their academic record.                                                                                                   |


### b. Use cases list

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
  * Admin click on “Create” button.
  * System create account.
* **Alternate Flow:**
  * Admin can create multiple accounts by clicking on “Add Account" button.
  * Admin fill in the form.
  * Admin click on “Create” button.
  * System create accounts.
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
  * System show list of accounts that match the search criteria.
* **Alternate Flow:**
  * Admin add search criteria by clicking on Search in” field.
  * Admin choose which criteria to search and combine with search by text.
  * system show list of accounts that match the search criteria.
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

#### UC-7 Admin change password of other account

* **Description:** Admin can change password of other account.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System change password of target account.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on “Account”.
  * System show list of all account.
  * Admin click on "Change Password" (lock icon) on actions column.
  * Admin input new password.
  * Admin click "Submit".
  * System change password of target account and show success message.
* **Alternate Flow:**
  * System displays notification if passowrd is invalid.
* **Exception:**
  * System displays notification if passowrd is invalid.


#### UC-8 Admin get grade report and get classification report in a year

* **Description:** Admin get grade report or classification report in a year.
* **Actors:** Admin
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
* **Postconditions:** System export report to admin's computer.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * At dashboard Admin choose year and grade to get report.
  * Admin click "Get Report" button.
  * System ready to export report to admin's computer.
  * Admin choose where to save export and click "Save".
* **Alternate Flow:**
  * Admin click "Get Classification Report" to get classification report.
  * System ready to export classification report to Admin's computer.
  * Admin choose where to save export and click "Save".
* **Exception:**
  * Button will be disabled if there is nothing to report.

#### UC-9 Admin get report of a class

* **Description:** Admin get report of a class.
* **Actors:** Admin
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
* **Postconditions:** System export report to admin's computer.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin choose "Classroom" on sidebar.
  * System show list of all clases.
  * Admin click on "Details" button on actions column to view detail of a class.
  * On details page Admin click "Get classroom report" button.
  * System ready to export report to admin's computer.
  * Admin choose where to save export and click "Save".
* **Exception:**
  * If class don't exist Admin will not able to get report.

#### UC-10 Admin view classrooms list

* **Description:** Admin can view list of all classrooms.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System show list of all classrooms.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on "Classroom" on sidebar.
  * System show list of all classrooms.
* **Alternate Flow:**
  * System displays notification “No classroom found” if there is no classroom.
* **Exception:**
  * System displays notification “No classroom found” if there is no classroom.

#### UC-11 Admin view classroom details

* **Description:** Admin can view details of a classroom.
* **Actors:** Admin
* **Preconditions:** 
  * Admin is logged in.
  * Classroom exists.
* **Postconditions:** System show details of a classroom.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on "Classroom" on sidebar.
  * System show list of all classrooms.
  * Admin click on "Details" button on actions column to view detail of a classroom.
  * System show details of a classroom.
* **Alternate Flow:**
  * System displays notification “Classroom not found” if classroom don't exist.
* **Exception:**
  * System displays notification “Classroom not found” if classroom don't exist.

### **Staff Features**
#### UC-12 Staff Login

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

#### UC-13 Staff view list of accounts

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
  * System displays notification There's nothing do show” if there is no account.
* **Exception:**
  * System displays notification “No account found” if there is no account.

#### UC-14 Staff view account details

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

#### UC-15 Staff search account

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
  * System show list of accounts that match the search criteria.
* **Alternate Flow:**
  * Admin add search criteria by clicking on Search in” field.
  * Admin choose which criteria to search and combine with search by text.
  * system show list of accounts that match the search criteria.
* **Exception:**
  * System displays notification “No account found” if there is no account that match the search criteria.

#### UC-16 Staff view class list

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

#### UC-17 Staff create new class

* **Description:** Staff create a new class.
* **Actors:** Staff
* **Preconditions:** Staff is logged in.
* **Postconditions:** System create a new class.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on “Classroom”.
  * Staff click on “Create” button.
  * A form will appear, staff then input class's information and choose homeroom teacher.
  * Staff click "Create classroom".
  * System create a new class and show success message.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### UC-18 Staff view class details

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

#### UC-19 Staff edit class

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

#### UC-20 Staff view student of a class

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

#### UC-21 Staff add students to a class

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
  * System add student to the class and show success message.
* **Alternate Flow:**
  * In add student form Staff click "Add student" to add more student.
  * Staff choose students to add to the class.
  * Staff click "Confirm".
  * System add students to the class and show success message.
* **Exception:**
  * System displays error notification if the form is not filled correctly.
  * System displays error notification if the student is already in the class.
  * System displays error notification if no student is selected.

#### UC-22 Staff view student details

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

#### UC-23 Staff edit student information

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
  * Staff click "Reset" button in case they want to reset the form.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### UC-24 Staff remove student from a class

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

#### UC-25 Staff view teacher of a class

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

#### UC-26 Staff assign teacher(s) to a class

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
  * A form will appear, staff then choose teacher and the subject they will teach.
  * Staff click "Confirm".
  * System add teacher to the class and show success message.
* **Alternate Flow:**
  * Staff click "Add teacher" to add more teachers.
  * Staff choose teacher and subject.
  * Staff click "Confirm".
  * System add teachers to the class and show success message.
* **Exception:**
  * System displays error notification if the form is not filled correctly.
  * System displays error notification if the teacher is already in the class.
  * System displays error notification if no teacher is selected.
  * System displays error notification if no subject is selected.

#### UC-27 Staff remove teacher from a class

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

#### UC-28 Staff edit their profile

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
  * Staff click Change Password button to change their password.
  * A form will appear, staff then edit their password.
  * Staff click "Submit" button.
  * System edit staff's password and show success message.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### UC-29 Staff print student record

* **Description:** Staff print student's records.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Student exists.
* **Postconditions:** System will save a file for staff to print student's records.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Teacher login with username and password.
  * On classroom list Staff click on "Details" (icon) on actions column.
  * System show class details.
  * Staff click "Students".
  * System show list of students of the class.
  * Staff choose a student and click "Details" (icon) on actions column.
  * System show student details.
  * Staff click "Print Record" button at Record session of student profile.
  * System show print preview of student's records.
  * Staff click "Save" button.
  * System save student's records to teacher's computer.
  * Staff using printer to print student's records.
* **Alternate Flow:**
  * On save, staff click "Cancel" button to cancel.

#### UC-30 Staff get grade report and get classification report in a year

* **Description:** Staff get grade report or classification report in a year.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
  * Class exists.
* **Postconditions:** System export report to staff's computer.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * At dashboard Staff choose year and grade to get report.
  * Staff click "Get Report" button.
  * System ready to export report to staff's computer.
  * Staff choose where to save export and click "Save".
* **Alternate Flow:**
  * Staff click "Get Classification Report" to get classification report.
  * System ready to export classification report to staff's computer.
  * Staff choose where to save export and click "Save".
* **Exception:**
  * Button will be disabled if there is nothing to report.

### **Teacher Features**

#### UC-31 Teacher Login

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

#### UC-32 Teacher view their profile

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

#### UC-33 Teacher change their password

* **Description:** Teacher change their password.
* **Actors:** Teacher
* **Postconditions:** System successfully change their password.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * Teacher click on their avatar at bottom left of screen.
  * System display teacher's profile.
  * Teacher click "Change Password" button.
  * System display form to change password.
  * Teacher enter old password, new password and confirm new password.
  * Teacher click "Submit" button.
  * System change teacher's password and show success message.
* **Alternate Flow:**
  * Teacher click con "X" button to cancel.
* **Exception:**
  * System displays error notification if the password is invalid.

#### UC-34 Teacher view their classes

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

#### UC-35 Teacher view class details

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
  * At dashboard Teacher choose a class and click on "Details" (icon) on actions column.
  * System show class details.
* **Alternate Flow:**
  * System displays error notification if the class is not found.
* **Exception:**
  * System displays error notification if the class is not found.

#### UC-36 Teacher view students in a class

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

#### UC-37 Teacher view teachers in the class

* **Description:** Teacher view list of teachers who teach in the class.
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

#### UC-38 Teacher view Student details

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

#### UC-39 Teacher print student's records

* **Description:** Teacher export student's records.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** System export student's records.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard (*classroom list*) Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Students".
  * System show list of students of the class.
  * Teacher click "Details" (icon) on actions column.
  * System show student details.
  * Teacher scroll down to "Record" section.
  * Teacher choose class to print.
  * Teacher click "Print Record" button at Record session of student profile.
  * System show print preview of student's records.
  * Teacher click "Save" button.
  * System save student's records to teacher's computer.
  * Teacher then use printer to print saved file.
* **Alternate Flow:**
  * On save, teacher click "Cancel" to cancel the save.

#### UC-40 Subject teacher send request to edit student's grade

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

#### UC-41 Teacher upload Record using image

* **Description:** Teacher upload Record using image.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** System analyze and generate Record from the image.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard (*classroom list*) Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Students".
  * System show list of students of the class.
  * Teacher click "Details" (icon) on actions column.
  * System show student details.
  * Teacher click "Upload Record" button at Record session of student profile.
  * System show upload methods.
  * Teacher choose upload methods.
  * Teacher upload image.
  * System analyze and generate Record from the image.
  * Teacher click "Upload" button.
  * System save the Record.
* **Alternate Flow:**
  * If system can't recognize the image it's will show notification.
* **Exception:**
  * If system can't recognize the image it's will show notification.

#### UC-42 Teacher view list of Pending Records's Request and Approve or Reject

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

#### UC-43 Teacher view history of student's records changes

* **Description:** Teacher view history of student's records changes.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** System show history of student's records changes.
* **Flow of Events:**
  * Teacher go to EduBlock.
  * Teacher login with username and password.
  * On dashboard (*classroom list*) Teacher click on "Details" (icon) on actions column.
  * System show class details.
  * Teacher click "Students".
  * System show list of students of the class.
  * Teacher click "Details" (icon) on actions column.
  * System show student details.
  * Teacher scroll down to "Record" section.
  * Teacher hover on "History" button(icon) at Action columns of Record session.
  * System show history of student's records changes.
* **Alternate Flow:**
  * System displays nothing if there is no changes.
* **Exception:**
  * System displays nothing if there is no changes.

### **Student Features**

#### UC-44 Student login

* **Description:** Student can login to EduBlock.
* **Actors:** Student
* **Preconditions:** Student has an account.
* **Postconditions:** EduBlock bring student to dashboard.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student click "Login" at homepage.
  * System redirect student to login page.
  * Student enter username and password.
  * System check the credentials.
  * System bring student to dashboard.
* **Alternate Flow:**
  * System displays error notification if the credentials is not correct.
* **Exception:**
  * System displays error notification if the credentials is not correct.

#### UC-45 Student view list of class they are in

* **Description:** Student view list of class they are in.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
  * Student is in the class.
* **Postconditions:** System show list of class they are in.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard.
  * Classes are listed on the dashboard.
* **Alternate Flow:**
  * System displays "No class" if there is no class.
* **Exception:**
  * System displays "No class" if there is no class.

#### UC-46 Student view class details

* **Description:** Student view class details.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
  * Student is in the class.
* **Postconditions:** System show class details.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard.
  * Classes are listed on the dashboard.
  * Student click "Details" (icon) on actions column.
  * System show class details.
* **Alternate Flow:**
  * System displays "No class" if there is no class.
* **Exception:**
  * System displays "No class" if there is no class.

#### UC-47 Student view teachers in the class

* **Description:** Student view teachers in the class.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
  * Student is in the class.
* **Postconditions:** System show list of teachers in the class.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard.
  * Classes are listed on the dashboard.
  * Student click "Details" (icon) on actions column.
  * System show class details.
  * Student click "Teachers".
  * System show list of teachers in the class.
* **Alternate Flow:**
  * System displays "No teacher" if there is no teacher.
* **Exception:**
  * System displays "No teacher" if there is no teacher.

#### UC-48 Student view their profile

* **Description:** Student view their profile.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
  * Student is in the class.
* **Postconditions:** Student is able to view their profile.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard.
  * Student click on their avatar at bottom left corner.
  * System show student details.

#### UC-49 Student view their academic records

* **Description:** Student view their academic records.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
  * Student is in the class.
* **Postconditions:** System show their academic records.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard.
  * Student click on their avatar at bottom left corner.
  * System show student details.
  * Student scroll down to "Record" section.
  * Student view their academic records.
* **Alternate Flow:**
  * At dashboard, student click on "View My Record" (icon) on actions column.
  * System show their academic records.
  * Student view their academic records.
* **Exception:**
  * System displays "No record" if there is no record.

#### UC-50 Student send request to ask for re-check their academic records

* **Description:** Student send request to ask for re-check their academic records.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
* **Postconditions:** System send request of student.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard.
  * Student click on their avatar at bottom left corner.
  * System show student details.
  * Student scroll down to "Record" section.
  * Student click "Request record change" icon on action column.
  * System show form to send request.
  * Student fill the form and click "Submit".
  * System send request of student.
* **Alternate Flow:**
  * System display notification if the form is not filled correctly.
* **Exception:**
  * System display notification if the form is not filled correctly.

#### UC-51 Student create key for parent to view their academic profile and records

* **Description:** Student create key for parent to view their academic profile and records.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
* **Postconditions:** System create a key for student.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard.
  * Student click on manage verified key.
  * Student click "Create key" button.
  * System create a key for student.
  * The key is displayed on the screen.
  * Student copy the key and send it to parent.
  * Parent use the key to view student's academic profile and records.
* **Alternate Flow:**
  * On entering the key, system displays "Invalid key" if the key is invalid.
* **Exception:**
  * On entering the key, system displays "Invalid key" if the key is invalid.

## Functional Requirements
### System Functional Overview
The system is designed to provide a platform for school to manage their student's record, information with high security, fast and pivate. 

### Features
#### **Account Features**

* **User Login**
  * Use cases: UC-1, UC-12, UC-31, UC-44
  * Description: The system shall allow user to login to EduBlock using their account.
* **Create Account**
  * Use cases: UC-4
  * Description: System shall allow admin to create account for staff, teacher, student, parent.
* **View list of all accounts**
  * Use cases: UC-2, UC-13
  * Description: System shall allow admin and staff to view list of accounts.
* **View account's detail**
  * Use cases: UC-3, UC-14, UC-22, UC-32, UC-38, UC-48
  * Description: The system shall allow user to view account's detail.
* **Update profile**
  * Use cases: UC-6, UC-23, UC-28
  * Description: The system shall allow only admin and staff to update account's profile.
* **Update password**
  * Use cases: UC-7, UC-28, UC-33
  * Description: The system shall allow user to reset their password.

#### **Class Features**

* **View classroom list**
  * Use cases: UC-10, UC-16, UC-34, UC-45
  * Description: The system shall allow user to view list of classes filter by their role.
* **View classroom detail**
  * Use cases: UC-11, UC-18, UC-35, UC-46
  * Description: The system shall allow user to view class detail.
* **View student in class**
  * Use cases: UC-11, UC-20, UC-36
  * Description: The system shall allow user who have the right to view list of students in class.
* **View teacher in class**
  * Use cases: UC-11, UC-25, UC-36, UC-47
  * Description: The system shall allow user who have the right to view list of teachers in class.
* **Create classroom**
  * Use cases: UC-17
  * Description: The system shall allow staff to create new class
* **Update classroom detail**
  * Use cases: UC-19
  * Description: THe system shall allow only staff to update class detail.
* **Add student to class**
  * Use cases: UC-21
  * Description: The system shall allow only staff to add student to class.
* **Assign teacher to class**
  * Use cases: UC-26
  * Description: The system shall allow only staff to assign teacher to class.
* **Remove student from class**
  * Use cases: UC-24
  * Description: The system shall allow only staff to remove student from class.
* **Remove teacher from class**
  * Use cases: UC-27
  * Description: The system shall allow only staff to remove teacher from class.
#### **Record Features**

* **View student's record** (view, print)
  * Use cases: UC-22, UC-29, UC-38, UC-39, UC-48, UC-49
  * Description: The system shall allow user to view student's record and print the record.
* **Send request to change student's record**
  * Use cases: UC-40, UC-50
  * Description: The system shall allow student to send request to re-check their record.
* **View list of pending change requests** (view, approve, reject)
  * Use cases: UC-42
  * Description: The system shall allow homeroom teacher to view list of pending change requests and approve or reject the request.

#### **Student Key Features**

* **Student create verified key**
  * Use cases: UC-51
  * Description: The system shall allow student to create verified key for their parents to use it to view their academic profile and records.
  
## Non-Functional Requirements

### External Interfaces

#### **User Interfaces**

* **UI-1:** The system shall provide a user interface for admin manage all accounts.
* **UI-2:** The system shall provide a user interface for staff to manage classes.
* **UI-3:** The system shall provide a user interface for teacher to view classes and manage students, student's records.
* **UI-4:** The system shall provide a user interface for teacher to view list of requests to change student's records.
* **UI-5:** The system shall provide a user interface for student to view classes and view their records.
* **UI-6:** The system shall provide a user interface for parent to view their children's records.
* **UI-7:** The system shall provide a user interface for student to generate private key for their parents to view their records.
* **UI-8:** The system shall permit complete access to the system via a web browser.
* **UI-9:** The web-application shall permit complete navigation.
* **UI-10:** The web-application shall permit complete all functions.

#### **Hardware Interfaces**

* **HI-1:** The web-app shall be able to run on any device that can run a web browser.
* **HI-2:** Graphic card is required to upload student's academic record using image file.

#### **Software Interfaces**

* **SI-1:** Hyperledger Fabric network.
  * **SI-1.1:** The system shall initialize decentralized network using Mini-fabric smoothly.
  * **SI-1.2:** The network shall install chaincode in all peers smoothly.
* **SI-2:** EduBlock client
  
  The request server shall communicate with user interface through RESt API to perform following operations:

  * **SI-2.1:** The system shall allow user to login.
  * **SI-2.2:** The system shall allow user to view their profile.
  * **SI-2.3:** The system shall allow user to reset their password.
  * **SI-2.4:** The system shall allow Admin to perform CRUD operations on account.
  * **SI-2.5:** The system shall allow Staff to perform CRU operations on classes.
  * **SI-2.6:** Teacher to send request to change student's academic record.
  * **SI-2.7:** Teacher to approve or reject request to change student's academic record.
  * **SI-2.8:** Student to send request to re-check student's academic record.
  * **SI-2.9:** Student to upload student's academic record.


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








