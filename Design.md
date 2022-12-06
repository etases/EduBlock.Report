# Software Design Description

## Overall Description

### Assumptions


### Design Constraints


### Technology Suggestion



## System Architecture Design

### Overall Architecture

```{#fig-overall .plantuml caption="Overall architecture"}
@startuml

left to right direction

component "Chain Node 1" as CN1 #Aqua
component "Request Server 1" as RS1 #Lime
component "Frontend Server 1" as FS1
RS1 - CN1
FS1 - RS1

component "Chain Node 2" as CN2 #Aqua
component "Request Server 2" as RS2 #Lime
component "Frontend Server 2" as FS2
RS2 - CN2
FS2 - RS2

component "Chain Node 3" as CN3 #Aqua
component "Request Server 3" as RS3 #Lime
component "Frontend Server 3" as FS3
RS3 - CN3
FS3 - RS3

component ".." as E1 #Aqua
component ".." as E2 #Aqua

CN1 -- CN2
CN2 -- CN3

E1 -- CN1
CN3 -- E2

@enduml
```

| Component       | Description                                                                                                                                                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Chain Node (CN) | A node of the blockchain. This stores the records and handles the history and transaction requests from the Request Server (Change/View the score, information, etc.)                                                              |
| Request Server  | The off-chain backend of a CN. This stores the pending requests from the user and is the only way to call a request to the CN. Each Request Server may have a different way to handle user requests (Voting, Direct Request, etc.) |
| Frontend Server | Provide the UX/UI for interacting with the Request Server                                                                                                                                                                          |

### System Architecture


### Package Diagram

```{#fig-package .plantuml caption="Package Diagram of Request Server"}
@startuml
skinparam linetype ortho

package root {
    node RequestServer as RS
    node DatabaseManager as Database

    package api {
        entity ServerHandler as SH
        entity StudentUpdater as SU
    }
    package entity {
        entity Account
        entity Student
        entity Classroom
        entity Record
        entity RecordEntry
        entity "..." as blank1
    }
    package handler {
        node AccountHandler
        node ClassroomHandler
        node RecordHandler
        node FabricHandler
        node StudentUpdateHandler
        node "..." as blank2
    }
    package internal {
        package student
        package "..."
    }
    package model {
        package input
        package output
        package fabric
    }
}
StudentUpdateHandler --> FabricHandler : access
student -d-> SU : import
Database -u-> entity : import
handler -d-> internal : access
handler --> model : import
handler -u-> entity : access
student -u-> fabric : access
RS --> handler : import
handler -u-> SH : import
@enduml
```

| Package Name     | Description                                          |
| ---------------- | ---------------------------------------------------- |
| root             | Main classes                                         |
| api              | The abstract classes & interfaces                    |
| entity           | The entities of the database                         |
| handler          | The handlers of the endpoints of the REST API server |
| internal         | Internal classes used by other packages              |
| internal/student | The instances of the Student Updater                 |
| model            | The input / output objects                           |
| model/input      | The input objects for the handlers                   |
| model/output     | The output objects returned from the handlers        |
| model/fabric     | The models used internally by the student updater    |

## System Detailed Design

### Class Specification

![Class Diagram of the Request Server](images/ClassDiagram.svg){#fig-class}

### Account

| Field Name                    | Type                    | Description                                                                                                   |
| ----------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------- |
| id                            | long                    | The account id                                                                                                |
| username                      | String                  | The username                                                                                                  |
| hashedPassword                | String                  | The hashed password                                                                                           |
| salt                          | String                  | The salt of the password                                                                                      |
| role                          | String                  | The role of the account                                                                                       |
| createdAt                     | Date                    | The date when the account was created                                                                         |
| classrooms                    | List ClassTeacher       | The list of references to the classrooms that the account participates if its role is Teacher                 |
| recordEntries                 | List RecordEntry        | The list of record entries related to the subjects the the account is teaching if its role is Teacher         |
| requestedRecordEntries        | List RecordEntry        | The list of verified record entries that the account requested to changes                                     |
| approvedRecordEntries         | List RecordEntry        | The list of verified record entries that the account accepted                                                 |
| pendingRecordEntries          | List PendingRecordEntry | The list of pending record entries related to the subjects the the account is teaching if its role is Teacher |
| requestedPendingRecordEntries | List PendingRecordEntry | The list of pending record entries that the account requested to changes                                      |
| homeClassrooms                | List Classroom          | The list of classrooms the the account is a homeroom teacher at                                               |

### Profile

| Field Name | Type    | Description                                                                     |
| ---------- | ------- | ------------------------------------------------------------------------------- |
| id         | long    | The account id                                                                  |
| account    | Account | The reference to the Account object                                             |
| firstName  | String  | The first name                                                                  |
| lastName   | String  | The last name                                                                   |
| male       | boolean | Is the person male? false if she is a female                                    |
| avatar     | String  | The link to the avatar image                                                    |
| birthDate  | Date    | The date of the birthday                                                        |
| address    | String  | The address                                                                     |
| phone      | String  | The phone number                                                                |
| email      | String  | The email                                                                       |
| updated    | boolean | The flag indicates that the profile requires sychronization with the Chain Node |

### Student

| Field Name   | Type              | Description                                                                                        |
| ------------ | ----------------- | -------------------------------------------------------------------------------------------------- |
| id           | long              | The account id                                                                                     |
| account      | Account           | The reference to the Account object                                                                |
| ethnic       | String            | The ethnic of the student                                                                          |
| fatherName   | String            | The name of the father of the student                                                              |
| fatherJob    | String            | The job of the father of the student                                                               |
| motherName   | String            | The name of the mother of the student                                                              |
| motherJob    | String            | The job of the mother of the student                                                               |
| guardianName | String            | The name of the guardian of the student                                                            |
| guardianJob  | String            | The job of the guardian of the student                                                             |
| homeTown     | String            | The home town of the student                                                                       |
| classrooms   | List ClassStudent | The list of references to the classrooms that the student participates                             |
| records      | List Record       | The list of records related to the classrooms that the student participates                        |
| updaterKey   | List UpdaterKey   | The list of updater keys of the student. Used to allow outsiders to get infomation of the student. |

### Classroom

| Field Name      | Type              | Description                                                              |
| --------------- | ----------------- | ------------------------------------------------------------------------ |
| id              | long              | The classroom id                                                         |
| name            | String            | The name of the classroom                                                |
| grade           | int               | The grade of the classroom                                               |
| year            | int               | The year of the classroom                                                |
| homeroomTeacher | Account           | The reference to the homeroom teacher of the classroom                   |
| students        | List ClassStudent | The list of references to the students that participate in the classroom |
| teachers        | List ClassTeacher | The list of references to the teachers that participate in the classroom |
| records         | List Record       | The list of records related to the classroom                             |

### ClassStudent

| Field Name | Type      | Description                    |
| ---------- | --------- | ------------------------------ |
| id         | long      | The id of the reference        |
| classroom  | Classroom | The reference to the classroom |
| student    | Student   | The reference to the student   |

### ClassTeacher

| Field Name | Type      | Description                                    |
| ---------- | --------- | ---------------------------------------------- |
| id         | long      | The id of the reference                        |
| classroom  | Classroom | The reference to the classroom                 |
| teacher    | Account   | The reference to the teacher                   |
| subjectId  | long      | The id of the subject that the teacher teaches |

### Record

| Field Name         | Type                    | Description                                               |
| ------------------ | ----------------------- | --------------------------------------------------------- |
| id                 | long                    | The record id                                             |
| classroom          | Classroom               | The reference to the classroom                            |
| student            | Student                 | The reference to the student                              |
| recordEntry        | List RecordEntry        | The list of verified record entries related to the record |
| pendingRecordEntry | List PendingRecordEntry | The list of pending record entries related to the record  |

### RecordEntry

| Field Name      | Type    | Description                                                            |
| --------------- | ------- | ---------------------------------------------------------------------- |
| id              | long    | The record entry id                                                    |
| subjectId       | long    | The id of the subject that the record entry is related to              |
| firstHalfScore  | int     | The score of the first semester of the subject                         |
| secondHalfScore | int     | The score of the second semester of the subject                        |
| finalScore      | int     | The final score of the subject                                         |
| requestDate     | Date    | The date when the record entry was requested                           |
| approvalDate    | Date    | The date when the record entry was approved                            |
| updateComplete  | boolean | The flag indicates that the record entry was updated to the Chain Node |
| teacher         | Account | The reference to the teacher that teaches the subject                  |
| requester       | Account | The reference to the account that requested the record entry           |
| approver        | Account | The reference to the account that approved the record entry            |
| record          | Record  | The reference to the record that the record entry is related to        |

### PendingRecordEntry

| Field Name      | Type    | Description                                                             |
| --------------- | ------- | ----------------------------------------------------------------------- |
| id              | long    | The pending record entry id                                             |
| subjectId       | long    | The id of the subject that the pending record entry is related to       |
| firstHalfScore  | int     | The score of the first semester of the subject                          |
| secondHalfScore | int     | The score of the second semester of the subject                         |
| finalScore      | int     | The final score of the subject                                          |
| requestDate     | Date    | The date when the pending record entry was requested                    |
| teacher         | Account | The reference to the teacher that teaches the subject                   |
| requester       | Account | The reference to the account that requested the pending record entry    |
| record          | Record  | The reference to the record that the pending record entry is related to |

### UpdaterKey

| Field Name | Type    | Description                                             |
| ---------- | ------- | ------------------------------------------------------- |
| id         | String  | The unique key                                          |
| student    | Student | The reference to the student that the key is related to |

### Sequence Diagram


## Data & Database Design

### Database Design

![Database Design of the Request Server](images/DatabaseDiagram.svg){#fig-db-design}

#### Account

| Field Name     | Type              | Size | Unique | Not Null | Flag | Notes |
| -------------- | ----------------- | ---- | ------ | -------- | ---- | ----- |
| ID             | bigint            |      | x      | x        | PK   |       |
| USERNAME       | character varying | 255  | x      | x        |      |       |
| HASHEDPASSWORD | character varying | 255  |        | x        |      |       |
| SALT           | character varying | 255  |        | x        |      |       |
| ROLE           | character varying | 255  |        | x        |      |       |
| CREATEDAT      | timestamp         |      |        | x        |      |       |

#### Profile

| Field Name  | Type              | Size | Unique | Not Null | Flag   | Notes                              |
| ----------- | ----------------- | ---- | ------ | -------- | ------ | ---------------------------------- |
| ACCOUNT\_ID | bigint            |      | x      | x        | PK, FK |                                    |
| ADDRESS     | character varying | 255  |        | x        |        |                                    |
| AVATAR      | character varying | 255  |        | x        |        |                                    |
| BIRTHDATE   | timestamp         |      |        | x        |        |                                    |
| EMAIL       | character varying | 255  |        | x        |        |                                    |
| FIRSTNAME   | character varying | 255  |        | x        |        |                                    |
| LASTNAME    | character varying | 255  |        | x        |        |                                    |
| MALE        | boolean           |      |        | x        |        |                                    |
| PHONE       | character varying | 255  |        | x        |        |                                    |
| UPDATED     | boolean           |      |        | x        |        | Used internally by student updater |

#### Student

| Field Name   | Type              | Size | Unique | Not Null | Flag   | Notes |
| ------------ | ----------------- | ---- | ------ | -------- | ------ | ----- |
| ACCOUNT\_ID  | bigint            |      | x      | x        | PK, FK |       |
| ETHNIC       | character varying | 255  |        | x        |        |       |
| FATHERJOB    | character varying | 255  |        | x        |        |       |
| FATHERNAME   | character varying | 255  |        | x        |        |       |
| GUARDIANJOB  | character varying | 255  |        | x        |        |       |
| GUARDIANNAME | character varying | 255  |        | x        |        |       |
| HOMETOWN     | character varying | 255  |        | x        |        |       |
| MOTHERJOB    | character varying | 255  |        | x        |        |       |
| MOTHERNAME   | character varying | 255  |        | x        |        |       |

#### Classroom

| Field Name          | Type              | Size | Unique | Not Null | Flag | Notes |
| ------------------- | ----------------- | ---- | ------ | -------- | ---- | ----- |
| ID                  | bigint            |      | x      | x        | PK   |       |
| NAME                | character varying | 255  |        | x        |      |       |
| GRADE               | character varying | 255  |        | x        |      |       |
| HOMEROOMTEACHER\_ID | bigint            |      |        | x        | FK   |       |
| START_YEAR          | integer           |      |        | x        |      |       |

#### Class Student

| Field Name    | Type   | Size | Unique | Not Null | Flag | Notes |
| ------------- | ------ | ---- | ------ | -------- | ---- | ----- |
| ID            | bigint |      | x      | x        | PK   |       |
| CLASSROOM\_ID | bigint |      |        | x        | FK   |       |
| STUDENT\_ID   | bigint |      |        | x        | FK   |       |

#### Class Teacher

| Field Name    | Type   | Size | Unique | Not Null | Flag | Notes                          |
| ------------- | ------ | ---- | ------ | -------- | ---- | ------------------------------ |
| ID            | bigint |      | x      | x        | PK   |                                |
| CLASSROOM\_ID | bigint |      |        | x        | FK   |                                |
| TEACHER\_ID   | bigint |      |        | x        | FK   |                                |
| SUBJECTID     | bigint |      |        | x        |      | Defined in the system's config |

#### Record

| Field Name           | Type   | Size | Unique | Not Null | Flag | Notes |
| -------------------- | ------ | ---- | ------ | -------- | ---- | ----- |
| ID                   | bigint |      | x      | x        | PK   |       |
| CLASSROOM\_ID        | bigint |      |        | x        | FK   |       |
| STUDENT\_ACCOUNT\_ID | bigint |      |        | x        | FK   |       |

#### Record Entry

| Field Name      | Type             | Size | Unique | Not Null | Flag | Notes                              |
| --------------- | ---------------- | ---- | ------ | -------- | ---- | ---------------------------------- |
| ID              | bigint           |      | x      | x        | PK   |                                    |
| RECORD\_ID      | bigint           |      |        | x        | FK   |                                    |
| REQUESTER\_ID   | bigint           |      |        |          | FK   |                                    |
| TEACHER\_ID     | bigint           |      |        |          | FK   |                                    |
| APPROVER\_ID    | bigint           |      |        |          | FK   |                                    |
| APPROVALDATE    | timestamp        |      |        | x        |      |                                    |
| REQUESTDATE     | timestamp        |      |        | x        |      |                                    |
| FIRSTHALFSCORE  | double precision |      |        | x        |      |                                    |
| SECONDHALFSCORE | double precision |      |        | x        |      |                                    |
| FINALSCORE      | double precision |      |        | x        |      |                                    |
| SUBJECTID       | bigint           |      |        | x        |      | Defined in the system's config     |
| UPDATECOMPLETE  | boolean          |      |        | x        |      | Used internally by student updater |

#### Pending Record Entry

| Field Name      | Type             | Size | Unique | Not Null | Flag | Notes                          |
| --------------- | ---------------- | ---- | ------ | -------- | ---- | ------------------------------ |
| ID              | bigint           |      | x      | x        | PK   |                                |
| RECORD\_ID      | bigint           |      |        | x        | FK   |                                |
| REQUESTER\_ID   | bigint           |      |        | x        | FK   |                                |
| TEACHER\_ID     | bigint           |      |        | x        | FK   |                                |
| REQUESTDATE     | timestamp        |      |        | x        |      |                                |
| FIRSTHALFSCORE  | double precision |      |        | x        |      |                                |
| SECONDHALFSCORE | double precision |      |        | x        |      |                                |
| FINALSCORE      | double precision |      |        | x        |      |                                |
| SUBJECTID       | bigint           |      |        | x        |      | Defined in the system's config |

#### Updater Key

| Field Name           | Type              | Size | Unique | Not Null | Flag | Notes |
| -------------------- | ----------------- | ---- | ------ | -------- | ---- | ----- |
| ID                   | character varying | 255  | x      | x        | PK   |       |
| STUDENT\_ACCOUNT\_ID | bigint            |      |        | x        | FK   |       |

### Data File Design

| File Name | Type   | Notes                                                |
| --------- | ------ | ---------------------------------------------------- |
| db        | Folder | The folder of The H2 Database files                  |
| updater   | Folder | Contains the data files of the local student updater |