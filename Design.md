# Software Design Description

## Overall Description

### Assumptions

- The target platform is a Docker-compatible operating system (Preferably Linux).
- The target web browser is Google Chrome.
- All products are run and operated in the same machine (Monolithic architecture).
- Only administrators can access the running system. Other users can only access the system through the frontend server.
- The blockchain is a private blockchain.
- The blockchain is an optional feature that can be turned on or off.
- The database is a H2 database.
- The mode of the database can be in-memory (for testing), file or remote (for production).

### Design Constraints

- The backend system is a REST API server.
- The backend system is a Java application.
- The blockchain is a Hyperledger Fabric blockchain.
- There should be an option to turn on or off the blockchain. If the blockchain is turned off, the backend system should still work as a normal REST API server with a local database.

### Technology Suggestion

- The endpoints of the backend system can be exposed so that a node browser can be developed to search & access the endpoints and get the necessary information.

## System Architecture Design

### Overall Architecture

```{#fig-overall .plantuml caption="Overall architecture"}
@startuml

left to right direction

component "Chain Node 1" as CN1 #Aqua
component "Request Server 1" as RS1 #Lime
component "Frontend Server 1" as FS1
RS1 . CN1
FS1 - RS1

component "Chain Node 2" as CN2 #Aqua
component "Request Server 2" as RS2 #Lime
component "Frontend Server 2" as FS2
RS2 . CN2
FS2 - RS2

component "Chain Node 3" as CN3 #Aqua
component "Request Server 3" as RS3 #Lime
component "Frontend Server 3" as FS3
RS3 . CN3
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

![Class Diagram of the Request Server](images/ClassDiagram.beautified.svg){#fig-class}

#### Account

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

#### Profile

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

#### Student

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

#### Classroom

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

#### ClassStudent

| Field Name | Type      | Description                    |
| ---------- | --------- | ------------------------------ |
| id         | long      | The id of the reference        |
| classroom  | Classroom | The reference to the classroom |
| student    | Student   | The reference to the student   |

#### ClassTeacher

| Field Name | Type      | Description                                    |
| ---------- | --------- | ---------------------------------------------- |
| id         | long      | The id of the reference                        |
| classroom  | Classroom | The reference to the classroom                 |
| teacher    | Account   | The reference to the teacher                   |
| subjectId  | long      | The id of the subject that the teacher teaches |

#### Record

| Field Name         | Type                    | Description                                               |
| ------------------ | ----------------------- | --------------------------------------------------------- |
| id                 | long                    | The record id                                             |
| classroom          | Classroom               | The reference to the classroom                            |
| student            | Student                 | The reference to the student                              |
| recordEntry        | List RecordEntry        | The list of verified record entries related to the record |
| pendingRecordEntry | List PendingRecordEntry | The list of pending record entries related to the record  |

#### RecordEntry

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

#### PendingRecordEntry

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

#### UpdaterKey

| Field Name | Type    | Description                                             |
| ---------- | ------- | ------------------------------------------------------- |
| id         | String  | The unique key                                          |
| student    | Student | The reference to the student that the key is related to |

#### StatisticKey

| Field Name | Type    | Description                                             |
| ---------- | ------- | ------------------------------------------------------- |
| id         | String  | The unique key                                          |
| year       | int     | The year that the key is referred to                    |
| grade      | int     | The grade that the key is referred to                   |

### Sequence Diagram

#### Create Account

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Account Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> RH : Generate unique account from request
RH -> DB : Store account
activate DB
DB --> RH : Return success
deactivate DB
RH --> RS : Wrap account to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Get Account

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Account Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get account
activate DB
alt Account exists
    DB --> RH : Return account
    RH --> RS : Wrap account to response
else Account does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
@enduml
```

#### Get Account List

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Account Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Fetch Accounts
activate DB
DB --> RH : Return Accounts
deactivate DB

alt Request has filters
    RH -> RH : Filter Accounts
end
RH --> RS : Wrap to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Display response
@enduml
```

#### Login

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Account Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get account by username
activate DB
alt Account does not exist
    DB --> RH : Return error
    RH --> RS : Wrap error to response
else Account exists
    DB --> RH : Return account
    deactivate DB
    RH -> RH : Verify password
    alt Password is correct
        RH -> RH : Generate account token
        RH --> RS : Wrap token to response
    else Password is incorrect
        RH --> RS : Wrap error to response
    end
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Update Account Password

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Account Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get account
activate DB
alt Account does not exist
    DB --> RH : Return error
    RH --> RS : Wrap error to response
else Account exists
    DB --> RH : Return account
    alt Own account
        RH -> RH : Verify old password
        alt Password is incorrect
            RH --> RS : Wrap error to response
        end
    end
    RH -> RH : Update new password
    RH -> DB : Update account
    DB --> RH : Return success
    deactivate DB
    RH --> RS : Wrap success to response
    deactivate RH
end
RS --> F : Send response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Update Account Profile

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Account Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get account
activate DB
alt Account does not exist
    DB --> RH : Return error
    RH --> RS : Wrap error to response
else Account exists
    DB --> RH : Return account
    alt Other account
        RH -> RH : Check if request can change the account
        alt Request cannot change
            RH --> RS : Wrap error to response
        end
    end
    RH -> RH : Update account profile
    RH -> DB : Update account
    DB --> RH : Return success
    deactivate DB
    RH --> RS : Wrap success to response
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Create Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> RH : Validate request
alt Invalid request
    RH --> RS : Wrap error to response
else Valid request
    RH -> RH : Generate classroom from request
    RH -> DB : Store classroom
    activate DB
    DB --> RH : Return success
    deactivate DB
    RH --> RS : Wrap classroom to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Add Students To Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Validate students
activate DB
alt Some students are not valid
    DB --> RH : Return error
    RH --> RS : Wrap error to response
else All students are valid
    DB --> RH : Return students
    RH -> DB : Get Classroom
    alt Classroom does not exist
        DB --> RH : Return error
        RH --> RS : Wrap error to response
    else Classroom exists
        DB --> RH : Return Classroom
        RH -> DB : Add students to Classroom
        DB --> RH : Return success
        deactivate DB
        RH --> RS : Wrap success to response
        deactivate RH
    end
end
RS --> F : Return response
deactivate RS
F --> U : Return response
deactivate F
@enduml
```

#### Remove Students From Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Remove pairs of student & classroom
activate DB
DB --> RH : Return success
deactivate DB
RH --> RS : Wrap success to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Return response
deactivate F
@enduml
```

#### Add Teachers To Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Validate teachers
activate DB
alt Some teachers are not valid
    DB --> RH : Return error
    RH --> RS : Wrap error to response
else All teachers are valid
    DB --> RH : Return teachers
    RH -> DB : Get Classroom
    alt Classroom does not exist
        DB --> RH : Return error
        RH --> RS : Wrap error to response
    else Classroom exists
        DB --> RH : Return Classroom
        RH -> DB : Add teachers to Classroom
        DB --> RH : Return success
        deactivate DB
        RH --> RS : Wrap success to response
        deactivate RH
    end
end
RS --> F : Return response
deactivate RS
F --> U : Return response
deactivate F
@enduml
```

#### Remove Teachers From Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Remove pairs of teacher & classroom
activate DB
DB --> RH : Return success
deactivate DB
RH --> RS : Wrap success to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Return response
deactivate F
@enduml
```

#### Update Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get classroom
activate DB
alt Classroom does not exist
    DB --> RH : Return error
    RH --> RS : Wrap error to response
else Classroom exists
    DB --> RH : Return classroom
    RH -> RH : Update classroom detail
    RH -> DB : Update classroom
    DB --> RH : Return success
    deactivate DB
    RH --> RS : Wrap success to response
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Get Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get classroom
activate DB
alt Classroom exists
    DB --> RH : Return classroom
    RH --> RS : Wrap classroom to response
else Classroom does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
@enduml
```

#### Get Classroom List

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Fetch Classrooms
activate DB
DB --> RH : Return Classrooms
deactivate DB

alt Request has filters
    RH -> RH : Filter Classrooms
end
RH --> RS : Wrap to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Display response
@enduml
```

#### Get Students In Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get classroom
activate DB
alt Classroom exists
    DB --> RH : Return classroom
    RH -> RH : Extract students from classroom
    RH --> RS : Wrap students to response
else Classroom does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
@enduml
```

#### Get Teachers In Classroom

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Classroom Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get classroom
activate DB
alt Classroom exists
    DB --> RH : Return classroom
    RH -> RH : Extract teachers from classroom
    RH --> RS : Wrap teachers to response
else Classroom does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
@enduml
```

#### Get Student Record

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Record Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Fetch Student Record
activate DB

alt Found
    DB --> RH : Return Student Record
    RH --> RS : Wrap Record to Response
else Not found
    DB --> RH : Return Error
    deactivate DB
    RH --> RS : Wrap Error to Response
    deactivate RH
end

RS --> F : Return Response
deactivate RS

alt Error
    F --> U : Display Error
else Export File
    F -> F : Export File
    F --> U : Download File
else Display
    F --> U : Display Response
end
deactivate F
@enduml
```

#### Get Student Record List

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Record Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Fetch Student Records
activate DB
DB --> RH : Return Student Records
deactivate DB

alt Request has filters
    RH -> RH : Filter Student Records
end
RH --> RS : Wrap to Response
deactivate RH
RS --> F : Return Response
deactivate RS

alt Export File
    F -> F : Map Response to File
    F --> U : Download File
else Display
    F --> U : Display Response
end
deactivate F
@enduml
```

#### Update Student Record

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Record Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Validate student & teacher permission
activate DB
alt Not Valid
    DB --> RH : Return error
    RH --> RS : Wrap error to Response
else Valid
    DB --> RH : Return student & record
    RH -> RH : Create Record Entry from Request
    RH -> DB : Save Record Entry
    DB --> RH : Return Created Response
    deactivate DB
    RH --> RS : Wrap response to Response
    deactivate RH
end
RS --> F : Return Response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Create Request To Update Student Record

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Record Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Validate student & record
activate DB
alt Not Valid
    DB --> RH : Return error
    RH --> RS : Wrap error to Response
else Valid
    DB --> RH : Return student & record
    RH -> DB : Create Pending Record Entry
    DB --> RH : Return Created Response
    deactivate DB
    RH --> RS : Wrap response to Response
    deactivate RH
end
RS --> F : Return Response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Get Pending Record Requests

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Record Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Fetch Pending Record Entries
activate DB
DB --> RH : Return Pending Record Entries
deactivate DB
RH --> RS : Wrap Entries to Response
deactivate RH
RS --> F : Return Response
deactivate RS
F --> U : Display Response
@enduml
```

#### Approve Pending Record Request

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Record Handler" as RH
database Database as DB

U -> F : Send verification request
activate F
F -> RS : Send verification request
activate RS
RS -> RH : Forward verification request
activate RH
RH -> DB : Check if pending record entry exists
activate DB
alt Exist
    DB --> RH : Return record entry
    RH -> DB : Remove record entry
    DB --> RH : Return success
    alt Accept pending record
        RH -> DB : Add verified record entry
        DB --> RH : Return success
    end
    RH --> RS : Return success response
else Not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Return error response
    deactivate RH
end
RS --> F : Return Response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Upload Record To Chain Node

```{.plantuml}
@startuml
database Database as DB
participant "Student Updater" as SU
participant "Chain Node" as CN
loop times to upload to Chain Node
    activate SU
    SU -> CN : Get record
    activate CN
    CN --> SU : Return record
    deactivate CN
    SU -> DB : Get verified record entries
    activate DB
    DB --> SU : Return verified record entries
    deactivate DB
    SU -> SU : Merge record
    SU -> CN : Upload merged record
    activate CN
    alt Success
        CN --> SU : Return success
        SU -> DB : Mark record entry as uploaded
        activate DB
        DB --> SU : Return success
        deactivate DB
    else Error
        CN --> SU : Return error
    end
    deactivate CN
    deactivate SU
end
@enduml
```

#### Create Statistic Key

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Generate Key from Request Data
activate DB
DB --> RH : Return Key
deactivate DB
RH --> RS : Wrap key to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml 
```

#### Get Statistic Key List

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get statistic key list
activate DB
DB --> RH : Return key list
deactivate DB
RH --> RS : Wrap key list to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml 
```

#### Delete Statistic Key

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get key
activate DB
alt Key exists
    DB --> RH : Return key
    RH -> DB : Remove key
    DB --> RH : Return success
    RH --> RS : Wrap success to response
else Key does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml 
```

#### Get Statistic Data

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB
participant "Student Updater" as SU

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get key
activate DB
alt Key exists
    DB --> RH : Return key
    RH -> RH : Extract grade & year from key
    RH -> SU : Get details for grade & year
    activate SU
    SU --> RH : Return details
    deactivate SU
    RH --> RS : Wrap details to response
else Key does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml 
```

#### Create Student Key

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Generate Key from Request Data
activate DB
DB --> RH : Return Key
deactivate DB
RH --> RS : Wrap key to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml 
```

#### Get Student Key List

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get student key list
activate DB
DB --> RH : Return key list
deactivate DB
RH --> RS : Wrap key list to response
deactivate RH
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml
```

#### Delete Student Key

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get key
activate DB
alt Key exists
    DB --> RH : Return key
    RH -> DB : Remove key
    DB --> RH : Return success
    RH --> RS : Wrap success to response
else Key does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml 
```

#### Get Student Data From Key

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "Request Server" as RS
participant "Student Update Handler" as RH
database Database as DB
participant "Student Updater" as SU

U -> F : Send request
activate F
F -> RS : Send request
activate RS
RS -> RH : Forward request
activate RH
RH -> DB : Get key
activate DB
alt Key exists
    DB --> RH : Return key
    RH -> RH : Extract student from key
    RH -> SU : Get details by student
    activate SU
    SU --> RH : Return details
    deactivate SU
    RH --> RS : Wrap details to response
else Key does not exist
    DB --> RH : Return error
    deactivate DB
    RH --> RS : Wrap error to response
    deactivate RH
end
RS --> F : Return response
deactivate RS
F --> U : Display response
deactivate F
@enduml 
```

#### Upload Legacy Student Record

```{.plantuml}
@startuml
autonumber

actor User as U
participant Frontend as F
participant "OCR Service" as OCR
participant "Request Server" as RS

U -> F : Send image
activate F
F -> OCR : Send image
activate OCR
alt Cannot recognize
  OCR --> F : Return Error
  F --> U : Display Error
else Recognized
  OCR --> F : Return Data
  deactivate OCR
  F --> U : Display Data
  U -> U : Edit / Correct Data
  group ref [Create Request To Update Student Record]
  U -> F : Send Data
  F -> RS : Send request
  activate RS
  RS --> F : Return Response
  deactivate RS
  F --> U : Display response
  deactivate F
end
@enduml
```

## Data & Database Design

### Database Design

![Database Design of the Request Server](images/DatabaseDiagram.Beautified.svg){#fig-db-design}

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

#### Statistic Key

| Field Name | Type              | Size | Unique | Not Null | Flag | Notes |
| ---------- | ----------------- | ---- | ------ | -------- | ---- | ----- |
| ID         | character varying | 255  | x      | x        | PK   |       |
| GRADE      | integer           |      |        | x        |      |       |
| START_YEAR | integer           |      |        | x        |      |       |

### Data File Design

| File Name | Type   | Notes                                                |
| --------- | ------ | ---------------------------------------------------- |
| db        | Folder | The folder of The H2 Database files                  |
| updater   | Folder | Contains the data files of the local student updater |