# FlowGuard - Testing Plan

## 1. Testing Objectives
The purpose of testing is to verify that FlowGuard performs project management and schedule analysis operations correctly.

## 2. Test Cases

| ID | Test Case | Expected Result |
|---|---|---|
| TC-01 | Create a project with valid data | Project is created |
| TC-02 | Create a task with valid data | Task is created |
| TC-03 | Enter a zero task duration | Validation error appears |
| TC-04 | Assign a task to a team member | Assignment is saved |
| TC-05 | Make a task depend on itself | Dependency is rejected |
| TC-06 | Create a circular dependency | Cycle is detected and rejected |
| TC-07 | Calculate a valid project schedule | CPM values are calculated |
| TC-08 | Analyze critical tasks | Critical path is identified |
| TC-09 | Simulate a task delay | New schedule is calculated |
| TC-10 | Compare baseline and scenario | Delay impact is displayed |

## 3. Testing Types
- Unit Testing
- Integration Testing
- Functional Testing
- User Interface Testing

## 4. Testing Tools
- pytest for Python unit testing.
- Manual testing for UI and workflows.

## 5. Testing Status
These are planned test cases. Results will be documented after implementation and execution.
