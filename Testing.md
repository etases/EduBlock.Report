# Software Testing Documentation

## Overall Description

### Test Model
We apply the V-model in our project, which is a development of the waterfall model. Testing is carried out concurrently with the software development cycle in the V-model, where a testing phase corresponds to a phase of software development.


### Testing Levels
About the Testing levels in our project, we apply all those levels including Unit testing, Integration testing, System testing and Acceptance testing.

With Unit testing, we test each small module in the system, each class and function.

With Integration testing is a type of testing in which individual software modules or functions are logically integrated and tested in groups together. For instance, we can test the interoperability of two functions, add 1 item and search for the item to see if they interact well with each other, after successfully creating an item, we can proceed to search for the newly created item. or not.

System testing is the last test phase to determine whether the system is about to deliver satisfying the requirements and goals. It tests the whole functionality and interface of the system. For instance, a database test for a system test is used to see if the data displayed on the system matches the data in the database.

Finally, with Acceptance Test, similar to System Test but usually tested by customers, the purpose is to see if the software meets the customer's requirements or not.


### Testing Types
Functional testing is checking if the system is working according to the business requirements and is performed in every level of testing.
Non-Functional testing is similar to Functional testing in that both occur in all levels of testing. Non-functional testing is primarily concerned with the software's other features, such as its security and if data is exposed by straightforward queries in any input field.
Structural testing is often considered a type of white box testing. Instead than focusing on the software's functionality, this method examines what is happening inside the program. Structural testing is also applicable at all testing levels.
Changes Testing is done to determine whether or not the program is functioning correctly after bugs have been fixed.


## Test Plan

### Test Stages
[Report_Test-Stages.xlsx](excel/Report_Test-Stages.xlsx)


### Resources

#### Human Resources
| Worker/ Doer | Role    | Specifice Responsibilities/Comments                 |
|--------------|---------|-----------------------------------------------------|
| TienHQ       |BE-Tester|Test if the Request Server is working properly or not|
| TuLX         |FE-Tester|Test if the ChainCode is working properly or not     |
| KhoaND       |Reporter |Handling reports related work                        |
| UyCHA        |BE-Tester|Test if the UI is working properly or not            |
| KhoiNM       |FE-Tester|Test if the UI is working properly or not            |


#### Environment
None


### Test Milestones
| Milestone Task | Effort (md) | Start Date | End Date   |
|----------------|-------------|------------|------------|
|ChainCode       |6            |Nov 9, 2022 |Nov 14, 2022|
|Request Server  |20           |Nov 15, 2022|Dec 04, 2022|


### Deliverables
| No | Deliverables               | Due Date     |
|----|----------------------------|--------------|
| 1  | Test Design                | Nov 11, 2022 |
| 2  | ChainCode Test script      | Nov 14, 2022 |
| 3  | Request Server Test script | Dec 15, 2022 |
| 4  | Test results               | Dec 16, 2022 |


## Test Cases
•	Unit Test Cases: [Report_Unit-Test-Case.xlsx](excel/Report_Unit-Test-Case.xlsx)

•	Other Test Cases: [Report_Test-Case-Document.xlsx](excel/Report_Test-Case-Document.xlsx)


## Test Reports
Test Report has been fully integrated in Unit_Test-Case and Test-Case-Document.
