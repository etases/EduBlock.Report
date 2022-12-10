# Software Requirement Specification

## Overall Description

### Product Overview

This is the software requirement specification for the project "EduBlock". EduBlock is an web-application that will help the school to manage their student's records, more specifically, the students and teachers can reduce paper's work to manage their records. Lately, the school has been using paper to manage their student's record, which is not efficient and not environmental friendly. EduBlock will help the school to manage their student's records in a more efficient way, although there are some other third party applications that can help school to keep their student's records nowdays, but it is not really efficient and safe, our application use blockchain technology to make sure the data is safe and secure. Every step of the process that need to be work with the records will be tracked by EduBlock, so the school can easily track the data changes and make sure the data is not being tampered.  


### Business Rules

| **ID** | **Rules Description**                                                                                                                                                                                                     |
| :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| BR-1   | The application will be used by the students, teachers, staff and admin.                                                                                                                                                  |
| BR-2   | Only Staff have permission to manage classroom including create new class, edit class, assign or remove teacher from the class, assign student to class, remove student from class, edit student information.             |
| BR-3   | Only Admin have permission to create new account(s).                                                                                                                                                                      |
| BR-4   | Only Teacher who teach the subject can edit the grade of the student.                                                                                                                                                     |
| BR-5   | Student can only view their class, profile and academic record.                                                                                                                                                           |
| BR-6   | In Blockchain, the data is immutable, so the data cannot be changed once it is created. Because of this, the data can just be append, can't be edit or delete, this will help ensure student's record is safe and secure. |
| BR-7   | A node if want to join the network, it must have other nodes permission or the node must be approved by the admin.                                                                                                        |
| BR-8   | In private blockchain, every node know each other, which node own the data. Data is shared between nodes so the data can be recovered if one node is down.                                                                |
| BR-9   | Other nodes can only read the data, they cannot change the data.                                                                                                                                                          |
| BR-10  | Third party member can only view the academic record and statistic of the students by using verified key.                                                                                                                 |




## User Requirements

* The Academic record management web-app has five active actors: Student, Teacher, Staff, Administrator and Third party's member (i.e. parents, etc.).
* Admin can create account for each role such as staff, student, teacher.
* Students can view their academic record.
* Teachers can manage their class and their students's academic record.
* Staff can manage the classroom and view the academic record of the students, assign or delete teacher from the class, assign student to class, create new class, edit student information.
* Third party's member can view the academic record and statistic of the students by using verified key.

:::{#fig-use-case-diagrams}

```{.plantuml caption="Admin"}
@startuml
left to right direction

(Login) as UC1
(View accounts) as UC2
(View account details) as UC3
(Create account) as UC4
(Search account) as UC5
(Update own profile) as UC6
(Change other account's password) as UC7
(Get grade report in a year) as UC8
(Get class report) as UC9
(View classroom list) as UC10
(View classroom details) as UC11
(Create statistic key) as UC12
:Admin: as A

A -- UC2
A -- UC3
A -- UC4
A -- UC5
A -- UC6
A -- UC7
A -- UC8
A -- UC9
A -- UC10
A -- UC11
A -- UC12

UC2 ..> UC1 : <<include>>
UC3 ..> UC1 : <<include>>
UC4 ..> UC1 : <<include>>
UC5 ..> UC1 : <<include>>
UC6 ..> UC1 : <<include>>
UC7 ..> UC1 : <<include>>
UC8 ..> UC1 : <<include>>
UC9 ..> UC1 : <<include>>
UC10 ..> UC1 : <<include>>
UC11 ..> UC1 : <<include>>
UC12 ..> UC1 : <<include>>
@enduml
```

```{.plantuml caption="Staff"}
@startuml
left to right direction

(Login) as UC13
(View account list) as UC14
(View account details) as UC15
(Search account) as UC16
(View classroom list) as UC17
(Create new classroom) as UC18
(View classroom details) as UC19
(Edit classroom) as UC20
(View students of a classroom) as UC21
(Add students to a classroom) as UC22
(View student details) as UC23
(Edit student details) as UC24
(Remove students from a classroom) as UC25
(View teachers of a classroom) as UC26
(Assign teachers to a classroom) as UC27
(Remove teachers from a classroom) as UC28
(Update own profile) as UC29
(Print student record) as UC30
(Get grade report in a year) as UC31
(Create statistic key) as UC32
:Staff: as A

A -- UC14
A -- UC15
A -- UC16
A -- UC17
A -- UC18
A -- UC19
A -- UC20
A -- UC21
A -- UC22
A -- UC23
A -- UC24
A -- UC25
A -- UC26
A -- UC27
A -- UC28
A -- UC29
A -- UC30
A -- UC31
A -- UC32

UC14 ..> UC13 : <<include>>
UC15 ..> UC13 : <<include>>
UC16 ..> UC13 : <<include>>
UC17 ..> UC13 : <<include>>
UC18 ..> UC13 : <<include>>
UC19 ..> UC13 : <<include>>
UC20 ..> UC13 : <<include>>
UC21 ..> UC13 : <<include>>
UC22 ..> UC13 : <<include>>
UC23 ..> UC13 : <<include>>
UC24 ..> UC13 : <<include>>
UC25 ..> UC13 : <<include>>
UC26 ..> UC13 : <<include>>
UC27 ..> UC13 : <<include>>
UC28 ..> UC13 : <<include>>
UC29 ..> UC13 : <<include>>
UC30 ..> UC13 : <<include>>
UC31 ..> UC13 : <<include>>
UC32 ..> UC13 : <<include>>
@enduml 
```

```{.plantuml caption="Teacher"}
@startuml
left to right direction

(Login) as UC33
(View own profile) as UC34
(Change own password) as UC35
(View classroom list) as UC36
(View classroom details) as UC37
(View students in a classroom) as UC38
(View teachers in a classroom) as UC39
(View student details) as UC40
(Print student records) as UC41
(Change student's score) as UC42
(Update Record using Image) as UC43
(View Pending record request) as UC44
(Approve / Reject record request) as UC44.1
(View record change history) as UC45
(Request to change student's score) as UC46
:Teacher: as A

A -- UC34
A -- UC35
A -- UC36
A -- UC37
A -- UC38
A -- UC39
A -- UC40
A -- UC41
A -- UC42
A -- UC43
A -- UC44
A -- UC44.1
A -- UC45
A -- UC46

UC44 <.. UC44.1: <<extend>>

UC34 ..> UC33 : <<include>>
UC35 ..> UC33 : <<include>>
UC36 ..> UC33 : <<include>>
UC37 ..> UC33 : <<include>>
UC38 ..> UC33 : <<include>>
UC39 ..> UC33 : <<include>>
UC40 ..> UC33 : <<include>>
UC41 ..> UC33 : <<include>>
UC42 ..> UC33 : <<include>>
UC43 ..> UC33 : <<include>>
UC44 ..> UC33 : <<include>>
UC44.1 ..> UC33 : <<include>>
UC45 ..> UC33 : <<include>>
UC46 ..> UC33 : <<include>>
@enduml 
```

```{.plantuml caption="Student"}
@startuml
left to right direction

(Login) as UC47
(View classroom list) as UC48
(View classroom details) as UC49
(View teachers in a classroom) as UC50
(View own profile) as UC51
(View own records) as UC52
(Request to change score) as UC53
(Create student key) as UC54
(Print own records) as UC55
(View record change history) as UC56
:Student: as A

A -- UC48
A -- UC49
A -- UC50
A -- UC51
A -- UC52
A -- UC53
A -- UC54
A -- UC55
A -- UC56

UC48 ..> UC47 : <<include>>
UC49 ..> UC47 : <<include>>
UC50 ..> UC47 : <<include>>
UC51 ..> UC47 : <<include>>
UC52 ..> UC47 : <<include>>
UC53 ..> UC47 : <<include>>
UC54 ..> UC47 : <<include>>
UC55 ..> UC47 : <<include>>
UC56 ..> UC47 : <<include>>
@enduml 
```

```{.plantuml caption="Third Party"}
@startuml
left to right direction

(View student profile & records) as UC57
(View grade statistics in a year) as UC58
:Third Party: as A

A -- UC57
A -- UC58
@enduml
```

Use case diagrams
:::

### System Actors

| **ID** | **Actor**   | **Description**                                                                                                                                                              |
| :----- | :---------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1      | ADMIN       | Admin is the person who has the highest authority in the system. Admin can manage the account of the other actors.                                                           |
| 2      | STAFF       | Staff is the person who has the authority to manage the classroom. Staff can assign or remove teacher from the class, assign student to class, remove student from class.    |
| 3      | TEACHER     | Teacher is the person who has the authority to manage their class. Teacher can view their students' academic record, subject teacher can send request to edit student grade. |
| 4      | STUDENT     | Student is the person who has the authority to view their academic record.                                                                                                   |
| 5      | THIRD PARTY | Third party is the person who has the authority to view the academic record and statistic of the students by using verified key.                                             |

### Use cases

#### **Admin Features**

##### UC-1 Admin Login

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

##### UC-2 Admin view list of accounts

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

##### UC-3 Admin view account details

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

##### UC-4 Admin create (multiple) account

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

##### UC-5 Admin search account

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

##### UC-6 Admin update their profile

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

##### UC-7 Admin change password of other account

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

##### UC-8 Admin get grade report and get classification report in a year

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

##### UC-9 Admin get report of a class

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

##### UC-10 Admin view classrooms list

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

##### UC-11 Admin view classroom details

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

##### UC-12 Admin Create statistic key

* **Description:** Admin can create statistic key for third party's member.
* **Actors:** Admin
* **Preconditions:** Admin is logged in.
* **Postconditions:** System create statistic key.
* **Flow of Events:**
  * Admin go to EduBlock.
  * Admin login with username and password.
  * Admin click on "Manage stats key list" on sidebar.
  * Admin choose grade and year.
  * Admin then click on "Create new Statistic key" button.
  * System create statistic key and show it on the list.
* **Alternate Flow:**
  * System displays notification if the key can't be created.
* **Exception:**
  * System displays notification if the key can't be created.

#### **Staff Features**

##### UC-13 Staff Login

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

##### UC-14 Staff view list of accounts

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

##### UC-15 Staff view account details

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

##### UC-16 Staff search account

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

##### UC-17 Staff view class list

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

##### UC-18 Staff create new class

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

##### UC-19 Staff view class details

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

##### UC-20 Staff edit class

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

##### UC-21 Staff view student of a class

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

##### UC-22 Staff add students to a class

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

##### UC-23 Staff view student details

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

##### UC-24 Staff edit student information

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

##### UC-25 Staff remove student from a class

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

##### UC-26 Staff view teacher of a class

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

##### UC-27 Staff assign teacher(s) to a class

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

##### UC-28 Staff remove teacher from a class

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

##### UC-29 Staff edit their profile

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

##### UC-30 Staff print student record

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

##### UC-31 Staff get grade report and get classification report in a year

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

##### UC-32 Staff create statistic key

* **Description:** Staff create statistic key for third party's member.
* **Actors:** Staff
* **Preconditions:** 
  * Staff is logged in.
* **Postconditions:** System create a statistic key.
* **Flow of Events:**
  * Staff go to EduBlock.
  * Staff login with username and password.
  * Staff click on "Manage stats key list" on sidebar.
  * Staff choose grade and year.
  * Staff then click on "Create new Statistic key" button.
  * System create statistic key and show it on the list.
* **Alternate Flow:**
  * System displays notification if the key can't be created.
* **Exception:**
  * System displays notification if the key can't be created.

#### **Teacher Features**

##### UC-33 Teacher Login

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

##### UC-34 Teacher view their profile

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

##### UC-35 Teacher change their password

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

##### UC-36 Teacher view their classes

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

##### UC-37 Teacher view class details

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

##### UC-38 Teacher view students in a class

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

##### UC-39 Teacher view teachers in the class

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

##### UC-40 Teacher view Student details

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

##### UC-41 Teacher print student's records

* **Description:** Teacher export student's records.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** System save student's records to teacher's computer.
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

##### UC-42 Subject teacher change student's score of their subject

* **Description:** Subject teacher change student's score.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is assigned to the class.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** Subject teacher successfully change student's score of their subject.
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
  * System show edit score form.
  * Teacher fill the form and click "Request" button.
  * System send request to edit student's score.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

##### UC-43 Teacher upload Record using image

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

##### UC-44 Teacher view list of Pending Records's Request and Approve or Reject

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

##### UC-45 Teacher view history of student's records changes

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

##### UC-46 Teacher request to change student's grade

* **Description:** Teacher request to change student's grade.
* **Actors:** Teacher
* **Preconditions:** 
  * Teacher is logged in.
  * Student exists.
  * Teacher is in the class.
  * Student is in the class.
* **Postconditions:** Teacher successfully request to change student's grade.
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
  * System send request to change student's grade to subject teacher.
* **Alternate Flow:**
  * System displays error notification if the form is not filled correctly.
* **Exception:**
  * System displays error notification if the form is not filled correctly.

#### **Student Features**

##### UC-47 Student login

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

##### UC-48 Student view list of class they are in

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

##### UC-49 Student view class details

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

##### UC-50 Student view teachers in the class

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

##### UC-51 Student view their profile

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

##### UC-52 Student view their academic records

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

##### UC-53 Student send request to ask for re-check their academic records

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

##### UC-54 Student create key for parent to view their academic profile and records

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

##### UC-55 Student print their academic records

* **Description:** Student print their academic records.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
* **Postconditions:** System save the academic records file to student's computer.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * System bring student to dashboard(classroom list).
  * At dashboard Student click on "View my record icon" on actions column corresponding to the class.
  * System show student details.
  * Student scroll down to "Record" section.
  * Student click "Print Record" button at bottom of the record table.
  * System show print preview.
  * System save the academic records file to student's computer.
  * Student then use printer to print the file.
* **Alternate Flow:**
  * System will cancel the save file process if the student click "Cancel" button.
* **Exception:**
  * System will cancel the save file process if the student click "Cancel" button.

##### UC-56 Student view history of their academic records's changes

* **Description:** Student view history of their academic records's changes.
* **Actors:** Student
* **Preconditions:** 
  * Student is logged in.
* **Postconditions:** System show history of their academic records's changes.
* **Flow of Events:**
  * Student go to EduBlock.
  * Student login with username and password.
  * At dashboard Student click on "View my record icon" on actions column corresponding to the class.
  * System show student details.
  * Student scroll down to "Record" section.
  * Student hover on "History" icon on action column.
  * System show history of their academic records's changes.
* **Alternate Flow:**
  * System displays nothing if there is no changes.
* **Exception:**
  * System displays nothing if there is no changes.

#### Third Party Features

##### UC-57 Third party view student's academic profile and records

* **Description:** Third party view student's academic profile and records by using verified key that student created without logging in.
* **Actors:** Third party
* **Preconditions:** 
  * Third party has the key.
* **Postconditions:** System show student's academic profile and records for third party's member.
* **Flow of Events:**
  * Third party go to EduBlock.
  * Third party enter the key.
  * System show student's academic profile and records for third party's member.
* **Alternate Flow:**
  * System displays "Invalid key" if the key is invalid.
* **Exception:**
  * System displays "Invalid key" if the key is invalid.

##### UC-58 Third party's member view statistics of a grade in a year

* **Description:** Third party's member view statistics of a grade in a year by using verified statistic key given by admin or staff.
* **Actors:** Third party's member
* **Preconditions:**
  * Staff or admin created the key. 
  * Third party's member has the key.
* **Postconditions:** System show statistics of a grade in a year for third party's member.
* **Flow of Events:**
  * Third party's member go to EduBlock.
  * Third party's member go to "Statistics key verification" page.
  * Third party's member enter the key.
  * System show statistics of a grade in a year for third party's member.
* **Alternate Flow:**
  * System displays "Invalid key" if the key is invalid.
* **Exception:**
  * System displays "Invalid key" if the key is invalid.

## Functional Requirements
### System Functional Overview
The system is designed to provide a platform for school to manage their student's record, information with high security, fast and pivate. 

### Features
#### **Account Features**

* **User Login**
  * Use cases: UC-1, UC-13, UC-32, UC-47
  * Description: The system shall allow user to login to EduBlock using their account.
* **Create Account**
  * Use cases: UC-4
  * Description: System shall allow admin to create account for staff, teacher, student, parent.
* **View list of all accounts**
  * Use cases: UC-2, UC-14
  * Description: System shall allow admin and staff to view list of accounts.
* **View account's detail**
  * Use cases: UC-3, UC-15, UC-23, UC-34, UC-40, UC-51
  * Description: The system shall allow user to view account's detail.
* **Update profile**
  * Use cases: UC-6, UC-24, UC-29
  * Description: The system shall allow only admin and staff to update account's profile.
* **Update password**
  * Use cases: UC-7, UC-29, UC-34
  * Description: The system shall allow user to reset their password.

#### **Class Features**

* **View classroom list**
  * Use cases: UC-10, UC-17, UC-36, UC-48
  * Description: The system shall allow user to view list of classes filter by their role.
* **View classroom detail**
  * Use cases: UC-11, UC-19, UC-37, UC-49
  * Description: The system shall allow user to view class detail.
* **View student in class**
  * Use cases: UC-11, UC-21, UC-38
  * Description: The system shall allow user who have the right to view list of students in class.
* **View teacher in class**
  * Use cases: UC-11, UC-26, UC-39, UC-50
  * Description: The system shall allow user who have the right to view list of teachers in class.
* **Create classroom**
  * Use cases: UC-18
  * Description: The system shall allow staff to create new class
* **Update classroom detail**
  * Use cases: UC-20 
  * Description: The system shall allow only staff to update class detail.
* **Add student to class**
  * Use cases: UC-22
  * Description: The system shall allow only staff to add student to class.
* **Assign teacher to class**
  * Use cases: UC-27
  * Description: The system shall allow only staff to assign teacher to class.
* **Remove student from class**
  * Use cases: UC-25
  * Description: The system shall allow only staff to remove student from class.
* **Remove teacher from class**
  * Use cases: UC-28
  * Description: The system shall allow only staff to remove teacher from class.
#### **Record Features**

* **View student's record** (view, print)
  * Use cases: UC-23, UC-30, UC-40, UC-41, UC-51, UC-52, UC-55
  * Description: The system shall allow user to view student's record and print the record.
* **Send request to change or re-check student's record**
  * Use cases: UC-46, UC-53
  * Description: The system shall allow student and homeroom teacher to send request to re-check or change their record.
* **View list of pending change requests** (view, approve, reject)
  * Use cases: UC-44
  * Description: The system shall allow homeroom teacher to view list of pending change requests and approve or reject the request.
* **View history of record's changes**
  * Use cases: UC-45, UC-56
  * Description: The system shall allow user to view history of record's changes.
* **Subject teacher change their subject score**
  * Use cases: UC-42
  * Description: The system shall allow subject teacher to change their subject score on student's record.

#### **Student Key Features**

* **Student create verified key**
  * Use cases: UC-51
  * Description: The system shall allow student to create verified key for their parents to use it to view their academic profile and records.
* **Third party's member view student's academic profile and records**
  * Use cases: UC-57
  * Description: The system shall allow third party's member to view student's academic profile and records by using verified key given by the student.
* **Third party's member view statistics of a grade in a year**
  * Use cases: UC-58
  * Description: The system shall allow third party's member to view statistics of a grade in a year by using verified statistic key given by admin or staff.
  
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








